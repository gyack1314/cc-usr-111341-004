# 业务资料约定

能耗单位kWh，排放因子kg CO2e/kWh，work_a/work_b是两种不互换的有效工作量单位。energy_blocks逐月归集总能耗；hardware和sla定义可比技术候选组，不默认可直接合并。

每行id在该表内唯一，文件顺序不代表业务事件顺序。清单schema=1，各表登记文件名、字节长度、SHA256、行数及完整字段集合，未知版本或内容变化应重新登记。金额及测量数值均为独立资料，不代表任何现实机构的经营数据。

- facilities：id、hardware、sla。
- monthly：id、facility、month、it_kwh、aux_kwh、work_a、work_b、available_hours。
- energy_blocks：id、monthly、kwh、kg_per_kwh。

normal与boundary是相互独立的资料包，不能直接拼接重复id。引用字段按本项目domain.py的REFERENCES登记。读取检查只检查完整性、身份及这些直接引用，不替代领域分析中的可识别性、时点可见性或可行性判断。
