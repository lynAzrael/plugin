# paracross 执行器 授权账户管理



## 执行逻辑

 1. 平行链申请开链之前申请几个授权账户，没有授权账户无法做跨链交易，目前没有押金机制
 1. 主链超级用户会分别向主链和平行链的manager合约发送账户添加tx，作为平行链的初始授权账户
 1. 平行链开链后在做跨链tx之前需要任何一个初始授权账户在平行链上发送takeover tx把初始授权账户接管到平行链，
    由平行链自己管理，如果不发送接管tx，平行链跨链无法完成
 1. 平行链接管初始授权账户后，初始授权账户审核后续新授权账户的添加和退出申请工作，必须除自己外，超过2/3数同意
    才可加入和退出，如果只剩最后一个账户，则不允许退出，如果随意退出有只留下僵尸授权账户风险，平行链失控
 1. 当前授权账户有投票删除某一个授权账户的权利，2/3数同意的规则
 1. 特殊或异常场景：
    1. 新申请节点还没投票就退出,不允许，必须都投完票之后再申请
    1. 申请节点退出后重新申请,允许重新加入，但需要重新投票   
    