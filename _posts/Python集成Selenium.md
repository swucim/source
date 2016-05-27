title: Python集成Selenium抓取动态网页示例
date: 2015-12-13 13:38:27
tags: [Selenium, 爬虫]
categories: Python
---
This is an example of crawling keywords related news from [人民网](http://www.people.com.cn) with selenium.

- You need to install Selenium package with 'pip install selenium' command;
- Additionally, you need to download selenium remote-server from selenium website, and then run command 'java -jar selenium-server-name.jar' to launch the server when crawling data.

```python
# -*- coding: utf-8 -*-
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
import time
import MySQLdb
import  pdb

def sql_query(sql_statement):
        conn=MySQLdb.connect(host='localhost',user='root',passwd='admin',db='renmin',port=3306,charset='utf8')
        cur = conn.cursor()
        sql = sql_statement
        try:
            cur.execute(sql)
            conn.commit()
            #print 'sql statement success'
        except StandardError, e:
            conn.rollback()
            print 'sql statement fail__'+sql_statement
def search_renmin(key_word,wait_seconds,all_flag):
    driver = webdriver.Firefox()
    driver.get('http://search.people.com.cn/rmw/GB/rmwsearch/')

    # set search key word, start/end date and each page number
    driver.find_element_by_class_name("tt09_input01").send_keys(key_word.decode('utf-8'))
    driver.find_element_by_name("PAGECOUNT").send_keys(80)
    driver.find_element_by_name("DATEFROM").send_keys("2012-12-01")
    driver.find_element_by_name("DATETO").send_keys("2015-12-07")
    # click seach
    driver.find_element_by_xpath('//div[@class="tt09"]/div[@style="width:90%;"]/input[@value="搜索"]').click()
    # element = driver.find_element_by_xpath('//div[@class="tt09"]/div[@style="width:90%;"]/input[@value="搜索"]')
    # ActionChains(driver).context_click(element).perform()
    counter = 1 #page counter
    search_page(driver, counter,key_word,wait_seconds,all_flag)
def search_page(driver, counter,key_word,wait_seconds,all_flag):
    time.sleep(wait_seconds) #waiting for page loading, pending on network status
    news_element = driver.find_elements_by_xpath('//div[@id="DETAILELE"]/table/tbody/tr/td[@class="f"]/a/font')
    link_element = driver.find_elements_by_xpath('//div[@id="DETAILELE"]/table/tbody/tr/td[@class="f"]/a')
    time_element = driver.find_elements_by_xpath('//div[@id="DETAILELE"]/table/tbody/tr/td[@class="f"]')
    content_element = driver.find_elements_by_xpath('//div[@id="DETAILELE"]/table/tbody/tr/td[@class="f"]/font')
    total_counter_element = driver.find_element_by_id("TOTALCOUNTELE")

    # get total records number
    total_counter = ''.join(total_counter_element.text.split("项".decode('utf-8'))[0][2:])
    # print int(total_counter)+1
    # each page fullfilled records counter
    record_counter = 0
    news_title,news_link,news_content,public_time = '','','',''
    for i in range(len(news_element)):
        if all_flag > 0:
            tempstr = time_element[i].text.strip()
            public_time = (''.join(tempstr[-20:])).strip().strip('-')
            news_title = news_element[i].text
            news_link = ''.join(link_element[i].get_attribute("href"))
            news_content = content_element[i].text.strip()
            record_counter = record_counter + 1
            sql = "insert into news2(title,link,content,time) values('%s','%s','%s','%s');"%\
                  (news_title,news_link,news_content,public_time)
            sql_query(sql)
        else:
            # if title contains key words then insert into db
            if key_word.decode('utf-8') in news_element[i].text:
                # get news public date and time
                tempstr = time_element[i].text.strip()
                public_time = (''.join(tempstr[-20:])).strip().strip('-')
                news_title = news_element[i].text
                news_link = ''.join(link_element[i].get_attribute("href"))
                news_content = content_element[i].text.strip()
                record_counter = record_counter + 1
                sql = "insert into news2(title,link,content,time) values('%s','%s','%s','%s');"%\
                      (news_title,news_link,news_content,public_time)
                sql_query(sql)

    print '---Page '+str(counter)+'---'+str(record_counter)+'/80 records fetched!----total:'+str(counter*80)+'/'+total_counter
    # click next page
    try:
        # recursive function
        if (counter+1)*80 < int(total_counter):
            driver.find_element_by_xpath('//div[@class="tt10b"]/table/tbody/tr[@id="PAGEELE"]/td[3]/input[1]').click()
            search_page(driver, counter+1,key_word,wait_seconds,all_flag)
        else:
            print 'fetch '+key_word.decode('utf-8')+' done!'
            driver.close()
            time.sleep(10)
    except StandardError, e:
        print e.message

# main function
if __name__ == "__main__":
    key_words = ["重庆","成都"]
    for k in key_words:
        print 'start searching: ' + k.decode('utf-8')
        # first parameter means key word
        # second parameter means waiting second for each time page loading
        # third parameter means if search in all contents, >0 for YES, =0 for NO
        search_renmin(k,20,0)
    print 'fetch all key words done!

```
