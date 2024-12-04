以下是将您提供的内容转换为Markdown格式的结果：

    # Getting Started
    
    ## Automated install (Linux/Unix/MacOS/FreeBSD/OpenBSD)
    
    ### To install with curl run the following command:
    
    ```bash
    curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
    

### To install with wget run the following command:

    wget --no-verbose -O - https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
    

### To install with fetch run the following command:

    fetch -o - https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
    

The script also accepts some options:
-------------------------------------

*   `-c` to use specified channel;
*   `-r` to reinstall AdGuard Home;
*   `-u` to uninstall AdGuard Home;
*   `-v` for verbose output.

**Note:** Options `-r` and `-u` are mutually exclusive.

DNS Servers
-----------

*   `tls://1dot1dot1dot1.cloudflare-dns.com`
*   `tls://1.1.1.1`
*   `https://cloudflare-dns.com/dns-query`
*   `https://1.1.1.1/dns-query`
*   `https://dns.google/dns-query`
*   `https://dns.google/resolve`
*   `https://[2001:4860:4860::64]/dns-query`
*   `https://[2001:4860:4860::6464]/dns-query`
*   `https://dns-unfiltered.adguard.com/dns-query`
*   `https://dns.adguard.com/dns-query`
*   `https://dns-family.adguard.com/dns-query`
*   `https://223.5.5.5/dns-query`
*   `https://223.6.6.6/dns-query`
*   `https://[2400:3200::1]/dns-query`
*   `https://[2400:3200:baba::1]/dns-query`
*   `https://dns.quad9.net/dns-query`
*   `https://dns9.quad9.net/dns-query`
*   `https://dns10.quad9.net/dns-query`
*   `https://dns11.quad9.net/dns-query`
*   `https://doh.opendns.com`
*   `https://doh.familyshield.opendns.com`

### Additional IP Addresses

*   `223.5.5.5`
*   `223.6.6.6`
*   `2400:3200::1`
*   `2400:3200:baba::1`
*   `8.8.8.8`
*   `8.8.4.4`
*   `2001:4860:4860::8888`
*   `2001:4860:4860::8844`

要设置AdGuard Home在Windows开机自启动，可以采用以下几种方法：

方法一：使用AdGuard Home自带的命令
AdGuard Home提供了一个命令行参数来实现开机自启动。你只需要在AdGuard Home的安装目录下，以管理员身份打开命令提示符，执行以下命令：

bash
.\AdGuardHome.exe -s install
这个命令会将AdGuard Home设置为Windows服务，使其在开机时自动启动
。
