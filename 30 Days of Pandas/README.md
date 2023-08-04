# leetcode-sql

## Pandas

### 单表

条件查找
* df = world[(world['area'] >= 1) | (world['population'] >= 2)]
* and：&
* or: |

获取字段(新建)
* return df[['name', 'population', 'area']]
* return pd.DataFrame({'rich_count': [len(df)]})

操作
* 去重：df.drop_duplicates(subset=['author_id'], inplace=True)
* 排序：df.sort_values(by=['author_id'], inplace=True)
* 重命名：df.rename(columns={'author_id': 'id'}, inplace=True) 将author_id改为id
* 获取前N条数据：df.head(N)
* 获取后N条数据：df.tail(N)
* transform() -> 'max', 'min', 'sum', 'mean', 'median', 'count(非NaN值的数量)', 'size(包括NaN值)'
* 数据排名：scores['rank'] = scores['score'].rank(method='dense', ascending=False)
* rank -> 'first',相同的值按顺序拍下去；'dense': 相同的值排名相同，下一个值排下一个位置

分类，group
* df.groupby('Department')['Salary'].transform('max') -> 根据Department分类，计算每个类中最大的Salary, 184
* 分类之后处理生成多列数据：1484, 1693

products.melt(id_vars=None, value_vars=None, var_name=None, value_name='value', col_level=None)
* value_vars: 要融化的列名
* var_name：新的列名，用于存储所有融化的列名
* value_name：新的列名，用与存储融化的列中原来的值
* 1795

DataFrame.loc[row_indexer, column_indexer]
* 过滤数据挑选出row_indexer行数，column_indexer列数的数据

长度（行的数量）
* len(df)
* df.shape[0]
* df.shape[1] -> 列的数量
* nunique() -> 去重之后的数量, 2356
* courses.groupby('class')['student'].nunique().reset_index()

### 多表

Filtering
* isin
* df = customers[~customers['id'].isin(orders['customerId'])] 
* 返回customers表，过滤掉customers['id']不在orders['customerId']中的数据

left join
* df = customers.merge(orders, left_on='id', right_on='customerId', how='left')
* 将orders表合并到customers中，根据customers中的id和orders中的customerId合并，不存在的id显示null
* 判断null: df = df[df['customerId'].isna()]

pd.concat(objs, axis=0, join='outer', ignore_index=False, keys=None)
* 连接多个表
* objs: [a, b, c], 要连接的表
* axis：连接方式，0垂直连接，1水平连接
* join：处理不存在的列，outer取并集，inner取交集
* ignore_index：是否保留原始索引
* 1795


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