# hello-world
just the begain
# 调用smtplib模块
import smtplib
# email 用于构建邮件内容
from email.header import Header
from email.mime.text import MIMEText
from_addr = 'XXXXXXX@qq.com'
# password是第三方识别码，并不是密码
password = 'XXXXX'
# 收信方邮箱
to_addr = 'XXXXXXX@qq.com'
# 发信服务器
smtp_server = 'smtp.qq.com'
# 邮箱正文内容，第一个参数为内容，第二个参数为格式(plain 为纯文本)，第三个参数为编码
text='''我想和你在一起，
        在某个小镇，
        共享无尽的黄昏，
        和绵绵不绝的钟声。
'''
msg = MIMEText(text,'plain','utf-8')
# 邮件头信息
msg['From'] = Header(from_addr)
msg['To'] = Header(to_addr) 
msg['Subject'] = Header('python test')
# 开启发信服务，这里使用的是加密传输
server = smtplib.SMTP_SSL(host=smtp_server)
server.connect(host=smtp_server,port=465)
# 登录发信邮箱
server.login(from_addr, password)
# 发送邮件
server.sendmail(from_addr, to_addr, msg.as_string())
# 关闭服务器
server.quit()
