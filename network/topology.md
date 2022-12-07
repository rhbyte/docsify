# 家庭网络

## 1.家庭原始网络布局

 交房时，已布好的网络使用的工程5类线，质量一般，网络布局见下图。

```mermaid
flowchart LR
    IN[入户]
    Box(弱电箱)
    a1([客厅网口1])
    a2([主卧网口1])
    a3([书房网口1])
    b1([客厅电话])
    b2([主卧电话])


    IN --光纤--> Box
    Box --网线3--> a3    
    Box --网线2--> a2
    Box -.电话线2>.-> b2    
    Box --网线1--> a1
    Box -.电话线1.-> b1    
    subgraph 书房
        a3
    end
    subgraph 主卧
        a2
        b2
    end
    subgraph 客厅
        a1
        b1
    end
```

 装修时重新部秋叶原六类非屏蔽网线。
 客厅增加2条网线，主卧、次卧、书房各增加一条网线，客厅、书房网线未接网络面板，留待备用，主卧网络面板保留。电话线均保留，如有需要可抽掉更换网线。装修后网络布局见下图。

```mermaid
flowchart LR
    IN[入户]
    Box(弱电箱)
    a1([客厅网口北1])
    a4([客厅网口北2])
    a5([客厅网口南])
    a2([主卧网口南])
    a6([主卧网口北])
    a3([书房网口1])
    a7([书房网口2])
    a8([次卧网口])
    b1([客厅电话])
    b2([主卧电话])


        IN --光纤--> Box
        Box --新网线5--> a8
        Box -.网线3.-> a3    
        Box --新网线4--> a7
        Box --网线2--> a2
        Box --新网线3--> a6
        Box -.电话线2.-> b2
        Box -.网线1.-> a1
        Box -.电话线1.-> b1
        Box --新网线1--> a4
        Box --新网线2--> a5

    subgraph 次卧
        a8    
    end    
    subgraph 书房
        a3
        a7
    end
    subgraph 主卧
        a2
        a6
        b2
    end
    subgraph 客厅
        a1
        b1
        a4
        a5
    end
```

## 2.网络拓扑图V1

 新房入住后，新增加了网络设备，相应的网络拓扑图见下图。光猫开启无线功能，手机、ipad通过光猫无线上网。

```mermaid
flowchart LR
    IN[入户]

    a1([客厅网口北1])
    a4([客厅网口北2])
    a5([客厅网口南])
    a2([主卧网口南])
    a6([主卧网口北])
    a3([书房网口1])
    a7([书房网口2])
    a8([次卧网口])
    %%b1([客厅电话])
    %%b2([主卧电话])

    c1{{光猫}}
    Box{{交换机}}
    c2{{台式机}}
    c3{{天猫魔盒}}
    c4{{服务器}}
    c5{{手机 ipad}}
    c7{{Sony}}

    IN --光纤--> c1
    subgraph 弱电箱        
        c1 --网线--> Box
    end    
    subgraph 客厅
        Box -.网线1.-> a1
        Box --新网线1--> a4 -->c4
        Box --新网线2--> a5 -->c3 -->c7
        c1 -.无线.-> c5
    end    
    subgraph 主卧
        Box --网线2--> a2
        Box --新网线3--> a6
    end
    subgraph 书房
        Box -.网线3.-> a3    
        Box --新网线4--> a7 -->c2
    end
    subgraph 次卧
        Box --新网线5--> a8    
    end    
```

## 3.网络拓扑图V2

 本次网络调整主要解决三个问题：1.无线网络覆盖；2.科学上网和外网访问；3.为今后网络拓展和智能家居打基础。

* 增加网络设备
  新增j4125工控主机、Redmi AX6000无线路由器，同时把以前的NetGear WNRD4300无线路由器重新启用。
  移动光猫改为桥接模式，关闭无线。由J4125做主路由，负责拨号。
  两个无线路由器做无线AP，负责无线设备接入，AX6000放客厅，WNRD4300放卧室，实现无线全覆盖。
  路由和无线接入分离，今后可以根据需要调整网络设备，并不需要在变更网络结构。
* 增加专用操作系统
  J4125主机安装PVE系统，PVE虚拟机安装iKuai、openwrt双路由和HomeAssistant。
  iKuai做主路由，负责pppoe拨号和内网DHCP，DHCP开启ipv6，同时开启动态域名，以便外网访问。
  openwrt做旁路由，安装科学上网插件，负责dns，安装广告拦截插件，负责广告过滤。
  HomeAssistant为后续智能家居接入做准备。
* 近期改进方案
  * 替换天猫魔盒为apple TV，作为视听中心和Homekit管理中心。
  * 升级J4125内存、硬盘，PVE虚拟机安装群晖，与服务器群晖重要资料互为备份，并常挂PT使用。
  * 服务器群晖配置一个大容量硬盘。

```mermaid
flowchart LR
    IN[入户]

    liv-net-n1([客厅网口北1])
    liv-net-n2([客厅网口北2])
    liv-net-s1([客厅网口南])
    bed1-net-s1([主卧网口南])
    bed1-net-n1([主卧网口北])
    book-net-1([书房网口1])
    book-net-2([书房网口2])
    bed2-net-1([次卧网口])
    %%b1([客厅电话])
    %%b2([主卧电话])

    modem{{光猫}}
    swich{{交换机}}
    PC{{台式机}}
    tmall{{天猫魔盒}}
    mobile{{手机 ipad}}
    redmi{{Redmi AX6000}}
    TV{{Sony TV}}
    WNRD{{WNRD 4300}}
    ikuai[/iKuai/]
    openwrt[/OpenWRT/]
    HA[/Homeassitant/]
    DSM{{群晖}}
    ilo[/iLO/]
    migate{{米家网关}}
    jellyfin[/jellyfin/]
    drive[/Drive/]

    IN --光纤--> modem
    subgraph 弱电箱

        modem --网线--> ikuai
        subgraph J4125
            subgraph PVE
                ikuai --> HA
                ikuai --> openwrt --> ikuai
            end
        end
        ikuai --网线--> swich
    end
    HA -.桥接.- migate
    swich --新网线5--> bed2-net-1    
    swich -.网线3.-> book-net-1
    swich --新网线4--> book-net-2
    swich --网线2--> bed1-net-s1
    swich --新网线3--> bed1-net-n1
    swich -.网线1.-> liv-net-n1
    swich --新网线1--> liv-net-n2
    swich --新网线2--> liv-net-s1

    subgraph 次卧
        bed2-net-1 --> ilo
        subgraph server
            subgraph esxi
                subgraph DSM
                    jellyfin
                    drive
                end
            end
            ilo
        end
    end    
    jellyfin <-.视频.-> mobile & PC
    drive <-.文件照片备份.-> PC & mobile

    subgraph 书房
        book-net-1    
        book-net-2 --网线-->PC
    end

    subgraph 主卧
        bed1-net-n1 --网线-->WNRD
        bed1-net-s1
    end    
    WNRD -.无线.-> mobile

    subgraph 客厅
        liv-net-s1 --网线-->redmi
        liv-net-n1
        liv-net-n2         
        redmi -.无线.-> migate & tmall & TV 
   tmall --> TV
    end
    jellyfin <-.视频.-> tmall
    redmi -.无线.-> mobile
```
