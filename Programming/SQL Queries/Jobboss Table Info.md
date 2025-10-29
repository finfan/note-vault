
This text is used for AI assistance with queries
```txt
Packlist_Header
COLUMN_NAME	DATA_TYPE	CHARACTER_MAXIMUM_LENGTH	IS_NULLABLE
Packlist	varchar	8	NO
Customer_Vendor	varchar	10	YES
Invoice	varchar	50	YES
Ship_To	int	NULL	YES
Ship_Via	varchar	15	YES
Contact	int	NULL	YES
Packlist_Date	datetime	NULL	YES
Invoiced	bit	NULL	NO
Comment	text	2147483647	YES
Last_Updated	datetime	NULL	NO

packlist_Detail
COLUMN_NAME	DATA_TYPE	CHARACTER_MAXIMUM_LENGTH	IS_NULLABLE
Packlist_DetailKey	int	NULL	NO
Packlist_Detail	int	NULL	YES
Packlist	varchar	8	NO
Job	varchar	10	YES
PO_Number	varchar	20	YES
Original_Packlist	int	NULL	YES
Unit_Price	float	NULL	YES
Quantity	int	NULL	NO
Instructions	text	2147483647	YES
Note_Text	text	2147483647	YES
Last_Updated	datetime	NULL	NO

Job
JobCOLUMN_NAME	DATA_TYPE	CHARACTER_MAXIMUM_LENGTH	IS_NULLABLE
Job	varchar	10	NO
Sales_Rep	varchar	6	YES
Customer	varchar	10	YES
Ship_To	int	NULL	YES
Part_Number varchar 30 YES
Rev	varchar	10	YES
Description	varchar	30	YES
Ext_Description	text	2147483647	YES
Drawing	varchar	30	YES
Unit_Price	float	NULL	YES
Note_Text	text	2147483647	YES
Comment	text	2147483647	YES
Last_Updated	datetime	NULL	NO

Customer
COLUMN_NAME	DATA_TYPE	CHARACTER_MAXIMUM_LENGTH	IS_NULLABLE
Customer	varchar	10	NO
Sales_Rep	varchar	6	YES
Name	varchar	45	YES
Note_Text	text	2147483647	YES
Last_Updated	datetime	NULL	NO


Address
COLUMN_NAME	DATA_TYPE	CHARACTER_MAXIMUM_LENGTH	IS_NULLABLE
AddressKey	int	NULL	NO
Address	int	NULL	YES
Customer	varchar	10	YES
Vendor	varchar	10	YES
Status	varchar	8	NO
Type	varchar	5	NO
Ship_Via	varchar	15	YES
Ship_To_ID	varchar	6	YES
Line1	varchar	45	YES
Line2	varchar	45	YES
City	varchar	20	YES
State	varchar	3	YES
Zip	varchar	10	YES
Name	varchar	45	YES
Country	varchar	50	YES
Phone	varchar	20	YES
Fax	varchar	20	YES
Lead_Days	smallint	NULL	NO
Last_Updated	datetime	NULL	NO
Billable	bit	NULL	NO
Shippable	bit	NULL	NO
Cell_Phone	varchar	20	YES


```

*AI prompt to inform AI the table relationships

Yes, the information you've provided—along with the attached table structure file—is enough to run example queries involving foreign key relationships between these tables. You have clearly described the links:

- **packlist_header.Packlist** → **packlist_detail.Packlist**
- **packlist_detail.Job** → **job.Job**
- **job.Customer** → **customer.Customer**
- **packlist_header.ShipTo** → **address.Address**

With the column definitions and data types present, I can help you write JOIN queries, SELECT statements, or filters across these related tables. Let me know what kind of query or result you want to see, for example: