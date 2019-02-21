# 大的国家 big-countries
## 题目
<a href="https://leetcode-cn.com/problems/big-countries/">原题链接</a>  
SQL架构

	Create table If Not Exists World (name varchar(255), continent varchar(255), area int, population int, gdp int)
	Truncate table World
	insert into World (name, continent, area, population, gdp) values ('Afghanistan', 'Asia', '652230', '25500100', '20343000000')
	insert into World (name, continent, area, population, gdp) values ('Albania', 'Europe', '28748', '2831741', '12960000000')
	insert into World (name, continent, area, population, gdp) values ('Algeria', 'Africa', '2381741', '37100000', '188681000000')
	insert into World (name, continent, area, population, gdp) values ('Andorra', 'Europe', '468', '78115', '3712000000')
	insert into World (name, continent, area, population, gdp) values ('Angola', 'Africa', '1246700', '20609294', '100990000000')
这里有张 World 表

	+-----------------+------------+------------+--------------+---------------+
	| name            | continent  | area       | population   | gdp           |
	+-----------------+------------+------------+--------------+---------------+
	| Afghanistan     | Asia       | 652230     | 25500100     | 20343000      |
	| Albania         | Europe     | 28748      | 2831741      | 12960000      |
	| Algeria         | Africa     | 2381741    | 37100000     | 188681000     |
	| Andorra         | Europe     | 468        | 78115        | 3712000       |
	| Angola          | Africa     | 1246700    | 20609294     | 100990000     |
	+-----------------+------------+------------+--------------+---------------+
如果一个国家的面积超过300万平方公里，或者人口超过2500万，那么这个国家就是大国家。

编写一个SQL查询，输出表中所有大国家的名称、人口和面积。

例如，根据上表，我们应该输出:

	+--------------+-------------+--------------+
	| name         | population  | area         |
	+--------------+-------------+--------------+
	| Afghanistan  | 25500100    | 652230       |
	| Algeria      | 37100000    | 2381741      |
	+--------------+-------------+--------------+

##解题思路
这题考察的是对基础SQL语句的应用，就是一句简单的查询语句。  

两个条件满足一个就可以，所以在SQL的条件判断的where语句里用一个or判断一下。  

本题答案就简单的一行：

    select name, population, area from world where area > 3000000 or population > 25000000;
