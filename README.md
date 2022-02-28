# Project Data Analysis for Retail : Sales Report Performance

## Dataset by DQLab 
Dataset yang digunakan berisikan transaksi yang dilakukan pada tahun **2009** sampai dengan tahun **2012** dengan jumlah raw data sebanyak **5500**. Nama tabel yang digunakan yaitu **dqlab_sales_store**
<br>
Silahkan download dataset pada link berikut, untuk melakukan eksplorasi data atau analisis lainnya menggunakan dataset yang sama
<br>
[dataset](https://drive.google.com/drive/u/3/folders/1usg-DAXAbxKe4JBJlJEIEk0mwaRgr5EL)

<br>

## Project dan Penyelesaian :
1. Overall performance DQLab Store dari tahun 2009-2012 untuk mendapatkan total penjualan (sales) dan jumlah order (number_of_order) dari tahun 2009 sampai 2012 (years). 
> SELECT YEAR(order_date) years,
<br>SUM(sales) sales,
<br>COUNT(order_quantity) number_of_order
<br>FROM dqlab_sales_store
<br>WHERE order_status='Order Finished'
<br>GROUP BY years
<br>ORDER BY years ASC;

2. Overall performance untuk mendapatkan total penjualan (sales) berdasarkan sub category dari produk (product_sub_category) pada tahun 2011 dan 2012 saja (years) 
> SELECT YEAR(order_date) years,
<br>product_sub_category,
<br>SUM(sales) sales
<br>FROM dqlab_sales_store
<br>WHERE YEAR(order_date) BETWEEN 2011 AND 2012 
<br>AND order_status='Order Finished'
<br>GROUP BY years,product_sub_category
<br>ORDER BY years,sales DESC;

3. Perhitungan efektivitas dan efisinesi promosi berdasarkan tahun dan presentase burn rate (total dicount/total sales*100)
>SELECT YEAR(order_date) years, 
<br>SUM(sales) sales, 
<br>SUM(discount_value) promotion_value, 
<br>ROUND(SUM(discount_value)*100/SUM(sales),2)
<br>burn_rate_percentage
<br>FROM dqlab_sales_store
<br>WHERE order_status='Order Finished'
<br>GROUP BY 1;

4. Perhitungan efektivitas dan efisinesi promosi berdasarkan product sub category dan product category
>SELECT YEAR(order_date) years, product_sub_category, product_category,
<br>SUM(sales) sales,
<br>SUM(discount_value) promotion_value,
<br>ROUND(SUM(discount_value)*100/SUM(sales),2) burn_rate_percentage
<br>FROM dqlab_sales_store
<br>WHERE YEAR(order_date)=2012
<br>AND order_status='Order Finished'
<br>GROUP BY years, product_sub_category, product_category
<br>ORDER BY sales DESC;

5. Total transaksi setiap tahun yang dilakukan oleh customer
>SELECT YEAR(order_date) years,
<br>COUNT(DISTINCT customer) number_of_customer
<br>FROM dqlab_sales_store
<br>WHERE order_status='Order Finished'
<br>GROUP BY years;

<br>

## Visualisasi Data mengenai performance pada penjualan DQlab Store
<br> 
Visualisasi data terhadap performa penjualan yang dilakukan melalui tableau

[datavisualization](https://public.tableau.com/app/profile/renita.salshabila) 
