  ███╗   ███╗██╗   ██╗██╗  ██╗██╗
    ████╗ ████║██║   ██║██║ ██╔╝██║
    ██╔████╔██║██║   ██║█████╔╝ ██║
    ██║╚██╔╝██║██║   ██║██╔═██╗ ██║
    ██║ ╚═╝ ██║╚██████╔╝██║  ██╗██║
    ╚═╝     ╚═╝ ╚═════╝ ╚═╝  ╚═╝╚═╝

    Muki是一款基于EHole二次开发的资产指纹识别工具，在红队作战中，信息收集
是必不可少的环节。Muki在EHole基础上增加了以下增强功能：

    • 代理池支持：支持从文件加载多个代理地址，自动轮换使用
    • 智能去重：基于URL标准化的高级去重算法，提高扫描效率
    • 多格式导出：支持Excel和JSON格式的结果导出
    • 重点资产提取：自动识别并导出关键系统资产

    Muki旨在帮助红队人员在信息收集期间能够快速从C段、大量杂乱的资产中精准定位到
易被攻击的系统，从而实施进一步攻击。

使用示例：
  # 指纹识别模块
  ./muki finger -l targets.txt -o results.xlsx          # 从文件扫描并导出Excel
  ./muki finger -u http://example.com -o result.json    # 扫描单个目标并导出JSON
  ./muki finger -l targets.txt -P proxies.txt          # 使用代理池进行扫描
  ./muki finger -fofa "title=\"后台管理\"" -o results.xlsx  # 从FOFA搜索并扫描

  # FOFA提取模块
  ./muki fofaext -s "domain=\"example.com\"" -o targets.txt

主要功能参数说明：
  -l, --local     从本地文件读取资产进行指纹识别
  -u, --url       识别单个目标
  -f, --fip       从FOFA提取IP资产进行指纹识别
  -s, --fofa      从FOFA提取资产，支持FOFA所有语法
  -a, --hip       从Hunter提取IP资产进行指纹识别
  -b, --hunter    从Hunter提取资产，支持Hunter所有语法
  -o, --output    输出结果文件，支持.json和.xlsx格式
  -P, --proxy-pool 从文件加载代理池进行扫描
  -p, --proxy     指定单个代理进行扫描
