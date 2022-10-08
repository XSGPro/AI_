import urllib.request
import re
res = []
def find_link(url_1, url_2, now_deep, tar_deep):
    if (url_1 == url_2):
        return url_2
    if(tar_deep <= now_deep):
        return False
    url = url_1
    pattern1 = '<.*?(href="https://.*?").*?'
    headers = {'User-Agent', 'Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML,like Gecko) Chrome/64.0.3282.186 Safari/537.36'}
    opener = urllib.request.build_opener()
    opener.addheaders = [headers]
    try:
        data = opener.open(url).read().decode('utf8')
    except:
        return False
    content_href = re.findall(pattern1,data,re.I)
    if(len(content_href) == 0):
        return False
    for i in content_href:
        j = i[6:-1]
    tar = find_link(j, url_2, now_deep+1, tar_deep)
    if (tar != False and tar != True):
        res.append((now_deep,url_1,tar))
        return True
    return False
url_1 = "https://www.baidu.com/"
url_2 = "https://www.baidu.com/favicon.ico"
now_deep = 0
res.append((0,url_1))
print('ori:\n',url_1)
for tar_deep in range(5):
    find_link(url_1, url_2, now_deep, tar_deep)
    if (len(res) != 1):
        res.append((len(res),url_2))
        for n,i in enumerate(res):
            if i not in res[:n]:
                deep, url = i[0], i[1]
                if(url == url_2):
                    print('get:\n',url)
                else:
                    print(url)
        break
