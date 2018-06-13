---
title: スキーマの制限
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c62f934561fa4a6c352ff84b8c1201461c42de39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357258"
---
# <a name="schema-restrictions"></a><span data-ttu-id="dc5fd-102">スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="dc5fd-102">Schema Restrictions</span></span>
<span data-ttu-id="dc5fd-103">2 番目の省略可能なパラメーター、 **GetSchema**メソッドは、スキーマ情報の量を制限するために使用される制限が返されに渡される、 **GetSchema**文字列の配列としてメソッド.</span><span class="sxs-lookup"><span data-stu-id="dc5fd-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="dc5fd-104">配列での位置により、渡すことができる値が決定します。これは、制限の番号に相当します。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="dc5fd-105">たとえば、次の表は、.NET Framework Data Provider for SQL Server を使用して、"Tables" スキーマ コレクションによりサポートされる制限を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="dc5fd-106">SQL Server スキーマ コレクションの追加の制限をこのトピックの終わりに示します。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="dc5fd-107">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-107">Restriction Name</span></span>|<span data-ttu-id="dc5fd-108">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-108">Parameter Name</span></span>|<span data-ttu-id="dc5fd-109">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-109">Restriction Default</span></span>|<span data-ttu-id="dc5fd-110">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-111">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-112">TABLE_CATALOG</span></span>|<span data-ttu-id="dc5fd-113">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-113">1</span></span>|  
|<span data-ttu-id="dc5fd-114">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-114">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc5fd-116">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-116">2</span></span>|  
|<span data-ttu-id="dc5fd-117">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-117">Table</span></span>|@Name|<span data-ttu-id="dc5fd-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-118">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-119">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-119">3</span></span>|  
|<span data-ttu-id="dc5fd-120">TableType</span><span class="sxs-lookup"><span data-stu-id="dc5fd-120">TableType</span></span>|@TableType|<span data-ttu-id="dc5fd-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc5fd-121">TABLE_TYPE</span></span>|<span data-ttu-id="dc5fd-122">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="dc5fd-123">制限値の指定</span><span class="sxs-lookup"><span data-stu-id="dc5fd-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="dc5fd-124">"Tables" スキーマ コレクションの制限の 1 つを使用するには、4 つの要素を使って文字列の配列を作成してから、制限の番号と一致する要素内に値を配置します。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="dc5fd-125">たとえば、テーブルを制限によって返される、 **GetSchema** "Sales"スキーマ内のテーブルのみをメソッドに渡す前に"Sales"に配列の 2 番目の要素を設定する、 **GetSchema**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc5fd-126">`SqlClient` と `OracleClient` の制限のコレクションには、追加の `ParameterName` 列があります。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="dc5fd-127">制限の既定の列は、下位互換性のために存在してはいますが、現在は無視されています。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="dc5fd-128">制限の値を指定する場合、文字列置換ではなく、パラメーター付きのクエリを使って、SQL への注入攻撃のリスクを最小限にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc5fd-129">配列内の要素数は、指定したスキーマ コレクションでサポートされる制限数以下にする必要があります。そうでない場合、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="dc5fd-130">制限は最大数よりも小さい場合があります。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="dc5fd-131">指定されていない制限は、null (無制限) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="dc5fd-132">呼び出すことによってサポートされている制限の一覧を特定の .NET Framework マネージ プロバイダーを照会することができます、 **GetSchema** "Restrictions"は、制限のスキーマ コレクションの名前を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="dc5fd-133">これにより、コレクション名の一覧、制限の名前、既定の制限値、および制限の番号と共に、<xref:System.Data.DataTable> が返されます。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="dc5fd-134">例</span><span class="sxs-lookup"><span data-stu-id="dc5fd-134">Example</span></span>  
 <span data-ttu-id="dc5fd-135">次の例を使用する方法を示します、<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>の .NET Framework Data Provider for SQL Server メソッド<xref:System.Data.SqlClient.SqlConnection>に関する、すべてのテーブルに含まれているスキーマ情報を取得するクラス、 **AdventureWorks**サンプル データベース、および"Sales"スキーマ内のテーブルのみに返される情報を制限します。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="dc5fd-136">SQL Server スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="dc5fd-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="dc5fd-137">次の表に、SQL Server スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="dc5fd-138">Users</span><span class="sxs-lookup"><span data-stu-id="dc5fd-138">Users</span></span>  
  
|<span data-ttu-id="dc5fd-139">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-139">Restriction Name</span></span>|<span data-ttu-id="dc5fd-140">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-140">Parameter Name</span></span>|<span data-ttu-id="dc5fd-141">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-141">Restriction Default</span></span>|<span data-ttu-id="dc5fd-142">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-143">User_Name</span></span>|@Name|<span data-ttu-id="dc5fd-144">name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-144">name</span></span>|<span data-ttu-id="dc5fd-145">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="dc5fd-146">Databases</span><span class="sxs-lookup"><span data-stu-id="dc5fd-146">Databases</span></span>  
  
|<span data-ttu-id="dc5fd-147">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-147">Restriction Name</span></span>|<span data-ttu-id="dc5fd-148">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-148">Parameter Name</span></span>|<span data-ttu-id="dc5fd-149">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-149">Restriction Default</span></span>|<span data-ttu-id="dc5fd-150">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-151">名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-151">Name</span></span>|@Name|<span data-ttu-id="dc5fd-152">名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-152">Name</span></span>|<span data-ttu-id="dc5fd-153">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="dc5fd-154">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="dc5fd-154">Tables</span></span>  
  
|<span data-ttu-id="dc5fd-155">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-155">Restriction Name</span></span>|<span data-ttu-id="dc5fd-156">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-156">Parameter Name</span></span>|<span data-ttu-id="dc5fd-157">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-157">Restriction Default</span></span>|<span data-ttu-id="dc5fd-158">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-159">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-160">TABLE_CATALOG</span></span>|<span data-ttu-id="dc5fd-161">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-161">1</span></span>|  
|<span data-ttu-id="dc5fd-162">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-162">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc5fd-164">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-164">2</span></span>|  
|<span data-ttu-id="dc5fd-165">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-165">Table</span></span>|@Name|<span data-ttu-id="dc5fd-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-166">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-167">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-167">3</span></span>|  
|<span data-ttu-id="dc5fd-168">TableType</span><span class="sxs-lookup"><span data-stu-id="dc5fd-168">TableType</span></span>|@TableType|<span data-ttu-id="dc5fd-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc5fd-169">TABLE_TYPE</span></span>|<span data-ttu-id="dc5fd-170">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="dc5fd-171">列</span><span class="sxs-lookup"><span data-stu-id="dc5fd-171">Columns</span></span>  
  
|<span data-ttu-id="dc5fd-172">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-172">Restriction Name</span></span>|<span data-ttu-id="dc5fd-173">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-173">Parameter Name</span></span>|<span data-ttu-id="dc5fd-174">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-174">Restriction Default</span></span>|<span data-ttu-id="dc5fd-175">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-176">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-177">TABLE_CATALOG</span></span>|<span data-ttu-id="dc5fd-178">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-178">1</span></span>|  
|<span data-ttu-id="dc5fd-179">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-179">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc5fd-181">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-181">2</span></span>|  
|<span data-ttu-id="dc5fd-182">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-182">Table</span></span>|@Table|<span data-ttu-id="dc5fd-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-183">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-184">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-184">3</span></span>|  
|<span data-ttu-id="dc5fd-185">Column</span><span class="sxs-lookup"><span data-stu-id="dc5fd-185">Column</span></span>|@Column|<span data-ttu-id="dc5fd-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-186">COLUMN_NAME</span></span>|<span data-ttu-id="dc5fd-187">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="dc5fd-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="dc5fd-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="dc5fd-189">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-189">Restriction Name</span></span>|<span data-ttu-id="dc5fd-190">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-190">Parameter Name</span></span>|<span data-ttu-id="dc5fd-191">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-191">Restriction Default</span></span>|<span data-ttu-id="dc5fd-192">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-193">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-194">TABLE_CATALOG</span></span>|<span data-ttu-id="dc5fd-195">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-195">1</span></span>|  
|<span data-ttu-id="dc5fd-196">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-196">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc5fd-198">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-198">2</span></span>|  
|<span data-ttu-id="dc5fd-199">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-199">Table</span></span>|@Table|<span data-ttu-id="dc5fd-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-200">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-201">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-201">3</span></span>|  
|<span data-ttu-id="dc5fd-202">Column</span><span class="sxs-lookup"><span data-stu-id="dc5fd-202">Column</span></span>|@Column|<span data-ttu-id="dc5fd-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-203">COLUMN_NAME</span></span>|<span data-ttu-id="dc5fd-204">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="dc5fd-205">ビュー</span><span class="sxs-lookup"><span data-stu-id="dc5fd-205">Views</span></span>  
  
|<span data-ttu-id="dc5fd-206">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-206">Restriction Name</span></span>|<span data-ttu-id="dc5fd-207">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-207">Parameter Name</span></span>|<span data-ttu-id="dc5fd-208">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-208">Restriction Default</span></span>|<span data-ttu-id="dc5fd-209">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-210">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-211">TABLE_CATALOG</span></span>|<span data-ttu-id="dc5fd-212">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-212">1</span></span>|  
|<span data-ttu-id="dc5fd-213">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-213">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc5fd-215">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-215">2</span></span>|  
|<span data-ttu-id="dc5fd-216">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-216">Table</span></span>|@Table|<span data-ttu-id="dc5fd-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-217">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-218">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="dc5fd-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="dc5fd-219">ViewColumns</span></span>  
  
|<span data-ttu-id="dc5fd-220">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-220">Restriction Name</span></span>|<span data-ttu-id="dc5fd-221">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-221">Parameter Name</span></span>|<span data-ttu-id="dc5fd-222">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-222">Restriction Default</span></span>|<span data-ttu-id="dc5fd-223">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-224">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-225">VIEW_CATALOG</span></span>|<span data-ttu-id="dc5fd-226">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-226">1</span></span>|  
|<span data-ttu-id="dc5fd-227">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-227">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="dc5fd-229">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-229">2</span></span>|  
|<span data-ttu-id="dc5fd-230">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-230">Table</span></span>|@Table|<span data-ttu-id="dc5fd-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-231">VIEW_NAME</span></span>|<span data-ttu-id="dc5fd-232">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-232">3</span></span>|  
|<span data-ttu-id="dc5fd-233">Column</span><span class="sxs-lookup"><span data-stu-id="dc5fd-233">Column</span></span>|@Column|<span data-ttu-id="dc5fd-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-234">COLUMN_NAME</span></span>|<span data-ttu-id="dc5fd-235">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="dc5fd-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="dc5fd-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="dc5fd-237">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-237">Restriction Name</span></span>|<span data-ttu-id="dc5fd-238">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-238">Parameter Name</span></span>|<span data-ttu-id="dc5fd-239">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-239">Restriction Default</span></span>|<span data-ttu-id="dc5fd-240">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-241">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="dc5fd-243">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-243">1</span></span>|  
|<span data-ttu-id="dc5fd-244">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-244">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="dc5fd-246">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-246">2</span></span>|  
|<span data-ttu-id="dc5fd-247">名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-247">Name</span></span>|@Name|<span data-ttu-id="dc5fd-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="dc5fd-249">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-249">3</span></span>|  
|<span data-ttu-id="dc5fd-250">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dc5fd-250">Parameter</span></span>|@Parameter|<span data-ttu-id="dc5fd-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-251">PARAMETER_NAME</span></span>|<span data-ttu-id="dc5fd-252">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="dc5fd-253">手順</span><span class="sxs-lookup"><span data-stu-id="dc5fd-253">Procedures</span></span>  
  
|<span data-ttu-id="dc5fd-254">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-254">Restriction Name</span></span>|<span data-ttu-id="dc5fd-255">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-255">Parameter Name</span></span>|<span data-ttu-id="dc5fd-256">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-256">Restriction Default</span></span>|<span data-ttu-id="dc5fd-257">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-258">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="dc5fd-260">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-260">1</span></span>|  
|<span data-ttu-id="dc5fd-261">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-261">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="dc5fd-263">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-263">2</span></span>|  
|<span data-ttu-id="dc5fd-264">名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-264">Name</span></span>|@Name|<span data-ttu-id="dc5fd-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="dc5fd-266">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-266">3</span></span>|  
|<span data-ttu-id="dc5fd-267">型</span><span class="sxs-lookup"><span data-stu-id="dc5fd-267">Type</span></span>|@Type|<span data-ttu-id="dc5fd-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="dc5fd-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="dc5fd-269">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="dc5fd-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="dc5fd-270">IndexColumns</span></span>  
  
|<span data-ttu-id="dc5fd-271">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-271">Restriction Name</span></span>|<span data-ttu-id="dc5fd-272">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-272">Parameter Name</span></span>|<span data-ttu-id="dc5fd-273">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-273">Restriction Default</span></span>|<span data-ttu-id="dc5fd-274">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-275">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="dc5fd-276">db_name()</span></span>|<span data-ttu-id="dc5fd-277">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-277">1</span></span>|  
|<span data-ttu-id="dc5fd-278">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-278">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="dc5fd-279">user_name()</span></span>|<span data-ttu-id="dc5fd-280">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-280">2</span></span>|  
|<span data-ttu-id="dc5fd-281">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-281">Table</span></span>|@Table|<span data-ttu-id="dc5fd-282">o.name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-282">o.name</span></span>|<span data-ttu-id="dc5fd-283">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-283">3</span></span>|  
|<span data-ttu-id="dc5fd-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="dc5fd-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="dc5fd-285">x.name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-285">x.name</span></span>|<span data-ttu-id="dc5fd-286">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-286">4</span></span>|  
|<span data-ttu-id="dc5fd-287">Column</span><span class="sxs-lookup"><span data-stu-id="dc5fd-287">Column</span></span>|@Column|<span data-ttu-id="dc5fd-288">c.name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-288">c.name</span></span>|<span data-ttu-id="dc5fd-289">5</span><span class="sxs-lookup"><span data-stu-id="dc5fd-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="dc5fd-290">Indexes</span><span class="sxs-lookup"><span data-stu-id="dc5fd-290">Indexes</span></span>  
  
|<span data-ttu-id="dc5fd-291">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-291">Restriction Name</span></span>|<span data-ttu-id="dc5fd-292">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-292">Parameter Name</span></span>|<span data-ttu-id="dc5fd-293">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-293">Restriction Default</span></span>|<span data-ttu-id="dc5fd-294">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-295">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="dc5fd-296">db_name()</span></span>|<span data-ttu-id="dc5fd-297">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-297">1</span></span>|  
|<span data-ttu-id="dc5fd-298">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-298">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="dc5fd-299">user_name()</span></span>|<span data-ttu-id="dc5fd-300">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-300">2</span></span>|  
|<span data-ttu-id="dc5fd-301">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-301">Table</span></span>|@Table|<span data-ttu-id="dc5fd-302">o.name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-302">o.name</span></span>|<span data-ttu-id="dc5fd-303">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="dc5fd-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="dc5fd-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="dc5fd-305">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-305">Restriction Name</span></span>|<span data-ttu-id="dc5fd-306">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-306">Parameter Name</span></span>|<span data-ttu-id="dc5fd-307">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-307">Restriction Default</span></span>|<span data-ttu-id="dc5fd-308">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="dc5fd-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-310">assemblies.name</span></span>|<span data-ttu-id="dc5fd-311">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-311">1</span></span>|  
|<span data-ttu-id="dc5fd-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="dc5fd-312">udt_name</span></span>|@UDTName|<span data-ttu-id="dc5fd-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="dc5fd-313">types.assembly_class</span></span>|<span data-ttu-id="dc5fd-314">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="dc5fd-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="dc5fd-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="dc5fd-316">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-316">Restriction Name</span></span>|<span data-ttu-id="dc5fd-317">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-317">Parameter Name</span></span>|<span data-ttu-id="dc5fd-318">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-318">Restriction Default</span></span>|<span data-ttu-id="dc5fd-319">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-320">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="dc5fd-322">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-322">1</span></span>|  
|<span data-ttu-id="dc5fd-323">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-323">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="dc5fd-325">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-325">2</span></span>|  
|<span data-ttu-id="dc5fd-326">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-326">Table</span></span>|@Table|<span data-ttu-id="dc5fd-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-327">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-328">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-328">3</span></span>|  
|<span data-ttu-id="dc5fd-329">名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-329">Name</span></span>|@Name|<span data-ttu-id="dc5fd-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="dc5fd-331">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="dc5fd-332">SQL Server 2008 スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="dc5fd-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="dc5fd-333">次の表に、SQL Server 2008 スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="dc5fd-334">これらの制限は、.NET Framework 3.5 SP1 および SQL Server 2008 以降で有効です。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="dc5fd-335">これらの制限は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dc5fd-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="dc5fd-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="dc5fd-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="dc5fd-337">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-337">Restriction Name</span></span>|<span data-ttu-id="dc5fd-338">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-338">Parameter Name</span></span>|<span data-ttu-id="dc5fd-339">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-339">Restriction Default</span></span>|<span data-ttu-id="dc5fd-340">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-341">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-342">TABLE_CATALOG</span></span>|<span data-ttu-id="dc5fd-343">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-343">1</span></span>|  
|<span data-ttu-id="dc5fd-344">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-344">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc5fd-346">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-346">2</span></span>|  
|<span data-ttu-id="dc5fd-347">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-347">Table</span></span>|@Table|<span data-ttu-id="dc5fd-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-348">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-349">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="dc5fd-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="dc5fd-350">AllColumns</span></span>  
  
|<span data-ttu-id="dc5fd-351">制限の名前</span><span class="sxs-lookup"><span data-stu-id="dc5fd-351">Restriction Name</span></span>|<span data-ttu-id="dc5fd-352">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="dc5fd-352">Parameter Name</span></span>|<span data-ttu-id="dc5fd-353">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="dc5fd-353">Restriction Default</span></span>|<span data-ttu-id="dc5fd-354">制限の番号</span><span class="sxs-lookup"><span data-stu-id="dc5fd-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="dc5fd-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="dc5fd-355">Catalog</span></span>|@Catalog|<span data-ttu-id="dc5fd-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="dc5fd-356">TABLE_CATALOG</span></span>|<span data-ttu-id="dc5fd-357">1</span><span class="sxs-lookup"><span data-stu-id="dc5fd-357">1</span></span>|  
|<span data-ttu-id="dc5fd-358">Owner</span><span class="sxs-lookup"><span data-stu-id="dc5fd-358">Owner</span></span>|@Owner|<span data-ttu-id="dc5fd-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="dc5fd-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="dc5fd-360">2</span><span class="sxs-lookup"><span data-stu-id="dc5fd-360">2</span></span>|  
|<span data-ttu-id="dc5fd-361">テーブル</span><span class="sxs-lookup"><span data-stu-id="dc5fd-361">Table</span></span>|@Table|<span data-ttu-id="dc5fd-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-362">TABLE_NAME</span></span>|<span data-ttu-id="dc5fd-363">3</span><span class="sxs-lookup"><span data-stu-id="dc5fd-363">3</span></span>|  
|<span data-ttu-id="dc5fd-364">Column</span><span class="sxs-lookup"><span data-stu-id="dc5fd-364">Column</span></span>|@Column|<span data-ttu-id="dc5fd-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="dc5fd-365">COLUMN_NAME</span></span>|<span data-ttu-id="dc5fd-366">4</span><span class="sxs-lookup"><span data-stu-id="dc5fd-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc5fd-367">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc5fd-367">See Also</span></span>  
 [<span data-ttu-id="dc5fd-368">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="dc5fd-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
