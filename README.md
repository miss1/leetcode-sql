# leetcode-sql

## Pandas

### 单表

条件查找
* df = world[(world['area'] >= 1) | (world['population'] >= 2)]
* and：&
* or: |

获取字段
return df[['name', 'population', 'area']]

操作
* 去重：df.drop_duplicates(subset=['author_id'], inplace=True)
* 排序：df.sort_values(by=['author_id'], inplace=True)
* 重命名：df.rename(columns={'author_id': 'id'}, inplace=True) 将author_id改为id

### 多表

Filtering
* isin
* df = customers[~customers['id'].isin(orders['customerId'])] 
* 返回customers表，过滤掉customers['id']不在orders['customerId']中的数据

left join
* df = customers.merge(orders, left_on='id', right_on='customerId', how='left')
* 将orders表合并到customers中，根据customers中的id和orders中的customerId合并，不存在的id显示null
* 判断null: df = df[df['customerId'].isna()]

### 字符串
* len: tweets['content'].str.len()
* str.upper()
* str.lower()
* tweets['content'].str[0].str.upper()
* str.title() -> 首字母大写，后面的小写
* str.match(r'') 正则
* str.contains(r'', regex=True), regex表明是否使用正则匹配

### if else
* employees['bonus'] = employees.apply(lambda x: x['salary'] if x['employee_id'] % 2 and not x['name'].startswith('M') else 0, axis=1)