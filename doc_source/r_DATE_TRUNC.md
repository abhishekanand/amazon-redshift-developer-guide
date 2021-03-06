# DATE\_TRUNC Function<a name="r_DATE_TRUNC"></a>

The DATE\_TRUNC function truncates a time stamp expression or literal based on the date part that you specify, such as hour, week, or month\. DATE\_TRUNC returns the first day of the specified year, the first day of the specified month, or the Monday of the specified week\. 

## Syntax<a name="r_DATE_TRUNC-synopsis"></a>

```
DATE_TRUNC('datepart', timestamp)
```

## Arguments<a name="r_DATE_TRUNC-arguments"></a>

 *datepart*   
The date part to which to truncate the time stamp value\. See [Dateparts for Date or Time Stamp Functions](r_Dateparts_for_datetime_functions.md) for valid formats\. 

 *timestamp*   
A timestamp column or an expression that implicitly converts to a time stamp\.

## Return Type<a name="r_DATE_TRUNC-return-type"></a>

TIMESTAMP

## Example<a name="r_DATE_TRUNC-example"></a>

In the following example, the DATE\_TRUNC function uses the 'week' datepart to return the date for the Monday of each week\. 

```
select date_trunc('week', saletime), sum(pricepaid) from sales where
saletime like '2008-09%' group by date_trunc('week', saletime) order by 1;
date_trunc  |    sum
------------+------------
2008-09-01  | 2474899.00
2008-09-08  | 2412354.00
2008-09-15  | 2364707.00
2008-09-22  | 2359351.00
2008-09-29  |  705249.00
(5 rows)
```