hellokingssr@gmail.com

获取所目的地(出发城市ID，到达城市ID、分片键 此处没有供应商)

for(所有目的地) {
  获取出发城市名称
  获取目的地城市名称

  传入出发城市名称、到达城市名、分片键、查询按照出发站、到达站、供应商group 取出最大发车时间列表
  根据出发城市、到达城市获取已存在的预售天数记录

  按照 出发城市ID 到达地城市ID 出发站ID 目的站ID 供应商的md5值 对已存在的预售期进行分类Map key md5 value 已存在的预售期

  所有预售期记录ID 作为无效预售期ID

  for(发车时间列表)  {
    取出出发站ID
    取出到达站ID

    对比发车时间与当前时间间隔天数，得出可预订天数
    将出发城市ID 目的地城市ID 出发站ID 目的站ID 供应商得出md5值

    if(已存在预售期的map分类中不包含此md5值)  {
      添加到待新增列表中
    } else {
      //需要更新这个预售期

      从无效预售期列表中移除
      添加到待更新列表中
    }
  }
}






查询出发城市、到达城市

for(所有目的地) {

  根据出发城市、到达城市按照出发站、目的站、供应商分类 获取计划班次

  根据出发城市、到达城市按照出发站、目的站、供应商分类 获取已存在的预售期天数
  根据预售期List获取记录ID 作为无效ID集合

  for(计划班次表) {
    if(按照出发城市，到达城市、出发站、到达站、供应商不存在于已有的预售期列表) {
      添加到待新增列表
    }else {
      //需要更新
      //从无效集合中移除
    }
  }

  新增数据到数据库

  更新已有记录

  删除无效记录
}
