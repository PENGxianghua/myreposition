#-*- codeing = utf-8 -*-
#@Time : 2021/6/27 22:09
#@Author : 彭湘华
#@File : mysql.py
#@Software : PyCharm
#连接数据库
import pymysql
# 获取连接对象conn，建立数据库的连接
co = pymysql.connect(host='172.20.10.4',port=3306,user='root',passwd='root',db='pxh',charset='utf8')    # db:表示数据库名称
cur=co.cursor()       #接收
sql='select * from t1'      #生成游标
#查看sql语句
cur.execute(sql)
data=cur.fetchall()
print(data)
co.commit()
cur.close()         #关闭游标
#增加数据
cur=co.cursor(cursor=pymysql.cursors.DictCursor)
sql_insert='insert into t1(n1,n2,n3) values(99,"蠢猪","2021-06-01")'
cur.execute(sql_insert)
co.commit()
cur.close()
#删除数据
cur=co.cursor(cursor=pymysql.cursors.DictCursor)
sql_delete='delete from t1 where n1=33'
cur.execute(sql_delete)
co.commit()
cur.close()
co.close()
