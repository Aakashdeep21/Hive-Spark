# Hive-Spark
<p>In this project, we use <strong data-start="119" data-end="134">Apache Hive</strong> as the data warehousing solution and <strong data-start="172" data-end="188">Apache Spark</strong> as the data processing framework.</p>
<p><strong>&nbsp;</strong></p>
<p class="" data-start="131" data-end="189"><strong data-start="131" data-end="154">1. Customer Dataset</strong><br data-start="154" data-end="157" />This dataset contains 5 columns:</p>
<ul data-start="191" data-end="303">
<li class="" data-start="191" data-end="208">
<p class="" data-start="193" data-end="208"><code data-start="193" data-end="206">customer_id</code></p>
</li>
<li class="" data-start="209" data-end="233">
<p class="" data-start="211" data-end="233"><code data-start="211" data-end="231">customer_unique_id</code></p>
</li>
<li class="" data-start="234" data-end="264">
<p class="" data-start="236" data-end="264"><code data-start="236" data-end="262">customer_zip_code_prefix</code></p>
</li>
<li class="" data-start="265" data-end="284">
<p class="" data-start="267" data-end="284"><code data-start="267" data-end="282">customer_city</code></p>
</li>
<li class="" data-start="285" data-end="303">
<p class="" data-start="287" data-end="303"><code data-start="287" data-end="303">customer_state</code></p>
</li>
</ul>

![image1](https://github.com/user-attachments/assets/a8784c06-4cb1-4249-956b-143d24c12e24)


<p class="" data-start="305" data-end="364"><strong data-start="305" data-end="326">2. Orders Dataset</strong><br data-start="326" data-end="329" />This dataset consists of 8 columns:</p>
<ul data-start="366" data-end="577">
<li class="" data-start="366" data-end="380">
<p class="" data-start="368" data-end="380"><code data-start="368" data-end="378">order_id</code></p>
</li>
<li class="" data-start="381" data-end="398">
<p class="" data-start="383" data-end="398"><code data-start="383" data-end="396">customer_id</code></p>
</li>
<li class="" data-start="399" data-end="417">
<p class="" data-start="401" data-end="417"><code data-start="401" data-end="415">order_status</code></p>
</li>
<li class="" data-start="418" data-end="448">
<p class="" data-start="420" data-end="448"><code data-start="420" data-end="446">order_purchase_timestamp</code></p>
</li>
<li class="" data-start="449" data-end="472">
<p class="" data-start="451" data-end="472"><code data-start="451" data-end="470">order_approved_at</code></p>
</li>
<li class="" data-start="473" data-end="507">
<p class="" data-start="475" data-end="507"><code data-start="475" data-end="505">order_delivered_carrier_date</code></p>
</li>
<li class="" data-start="508" data-end="543">
<p class="" data-start="510" data-end="543"><code data-start="510" data-end="541">order_delivered_customer_date</code></p>
</li>
<li class="" data-start="544" data-end="577">
<p class="" data-start="546" data-end="577"><code data-start="546" data-end="577">order_estimated_delivery_date</code></p>
</li>
</ul>

![image](https://github.com/user-attachments/assets/776602b6-e372-49bf-8c2d-fd8a32555d4c)


## Hive Tables
<p>To begin with, we will create a dedicated database named <code data-start="320" data-end="332">hive_spark</code>. All subsequent tables will be created within this database.</p>
<p>&nbsp;</p>

```sql
create database hive_spark;
 ```

<p>"Now, we will create two Hive tables. The column structure of each table will mirror that of our source file."</p>

<p>Hive DDL (Data Definition Language) command to create a <code data-start="82" data-end="92">customers</code> table.</p>
```sql
create table hive_spark.customers(
customer_id string,
customer_unique_id string,
customer_zip_code_prefix string,
customer_city string,
customer_state string)
row format delimited
fields terminated by ','
tblproperties('skip.header.line.count'='1');
```
<p>Hive DDL (Data Definition Language) command to create a <span style="font-family: monospace;"><span style="background-color: #bfe6ff;">orders </span></span>table.</p>
```sql
create table hive_spark.orders(
order_id string,
customer_id string,
order_status string,
order_purchase_timestamp timestamp,
order_approved_at timestamp,
order_delivered_carrier_date timestamp,
order_delivered_customer_date timestamp,
order_estimated_delivery_date timestamp )
row format delimited
fields terminated by ','
tblproperties('skip.header.line.count'='1');
```
