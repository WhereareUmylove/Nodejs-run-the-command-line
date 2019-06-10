# Nodejs-run-the-command-line
怎么样在Nodejs中修改IE代理，这个方法是通过修改注册表完成对ID代理的修改，吊锤网上的一切瞎扯代码
<p>How to modify IE agent in Nodejs? This method is to modify the ID agent by modifying the registry, and all the bullshit code on the hammer network.</p>
</br></br>
<p>首先安装一下这个包   regedit------cnpm i --save regedit</p>
<p>引入 const regedit = require('regedit')</p>
代码
<p>//修改注册表，修改IE代理
  regedit.putValue({</br>
    'HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\': {</br>
      'ProxyServer': {</br>
        value: '192.168.1.3:8080',</br>
        type: 'REG_SZ'</br>
      }</br>
    },</br>
  }, function (err) {</br>
  })</br>
</p>
<p>//关闭IE代理
  regedit.putValue({</br>
    'HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\': {</br>
      'ProxyEnable': {</br>
        value: '0',</br>
        type: 'REG_DWORD'</br>
      }</br>
    },</br>
  }, function (err) {</br>
  })</br>
</p>
<p>//清空IE代理地址
  regedit.putValue({</br>
    'HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\': {</br>
      'ProxyServer': {</br>
        value: '',</br>
        type: 'REG_SZ'</br>
      }</br>
    },</br>
  }, function (err) {</br>
  })</br>
</p>
<p>ProxyServer表示你要修改的注册表的key</p>
<p>value表示你要修改的注册表的key的值</p>
<p>type表示你要修改的注册表的值的类型</p>
</br>
另外还有node-cmd这个库，运行命令行的，推荐看一下
