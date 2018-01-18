---
title: "スキーマの制限"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5b004b70716c61af8ac37fef76f660c488e5a74
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="schema-restrictions"></a><span data-ttu-id="96e2c-102">スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="96e2c-102">Schema Restrictions</span></span>
<span data-ttu-id="96e2c-103">2 番目の省略可能なパラメーター、 **GetSchema**メソッドは、スキーマ情報の量を制限するために使用される制限が返されに渡される、 **GetSchema**文字列の配列としてメソッド.</span><span class="sxs-lookup"><span data-stu-id="96e2c-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="96e2c-104">配列での位置により、渡すことができる値が決定します。これは、制限の番号に相当します。</span><span class="sxs-lookup"><span data-stu-id="96e2c-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="96e2c-105">たとえば、次の表は、.NET Framework Data Provider for SQL Server を使用して、"Tables" スキーマ コレクションによりサポートされる制限を示しています。</span><span class="sxs-lookup"><span data-stu-id="96e2c-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="96e2c-106">SQL Server スキーマ コレクションの追加の制限をこのトピックの終わりに示します。</span><span class="sxs-lookup"><span data-stu-id="96e2c-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="96e2c-107">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-107">Restriction Name</span></span>|<span data-ttu-id="96e2c-108">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-108">Parameter Name</span></span>|<span data-ttu-id="96e2c-109">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-109">Restriction Default</span></span>|<span data-ttu-id="96e2c-110">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-111">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-112">TABLE_CATALOG</span></span>|<span data-ttu-id="96e2c-113">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-113">1</span></span>|  
|<span data-ttu-id="96e2c-114">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-114">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="96e2c-116">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-116">2</span></span>|  
|<span data-ttu-id="96e2c-117">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-117">Table</span></span>|@Name|<span data-ttu-id="96e2c-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-118">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-119">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-119">3</span></span>|  
|<span data-ttu-id="96e2c-120">TableType</span><span class="sxs-lookup"><span data-stu-id="96e2c-120">TableType</span></span>|@TableType|<span data-ttu-id="96e2c-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="96e2c-121">TABLE_TYPE</span></span>|<span data-ttu-id="96e2c-122">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="96e2c-123">制限値の指定</span><span class="sxs-lookup"><span data-stu-id="96e2c-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="96e2c-124">"Tables" スキーマ コレクションの制限の 1 つを使用するには、4 つの要素を使って文字列の配列を作成してから、制限の番号と一致する要素内に値を配置します。</span><span class="sxs-lookup"><span data-stu-id="96e2c-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="96e2c-125">たとえば、テーブルを制限によって返される、 **GetSchema** "Sales"スキーマ内のテーブルのみをメソッドに渡す前に"Sales"に配列の 2 番目の要素を設定する、 **GetSchema**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="96e2c-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96e2c-126">`SqlClient` と `OracleClient` の制限のコレクションには、追加の `ParameterName` 列があります。</span><span class="sxs-lookup"><span data-stu-id="96e2c-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="96e2c-127">制限の既定の列は、下位互換性のために存在してはいますが、現在は無視されています。</span><span class="sxs-lookup"><span data-stu-id="96e2c-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="96e2c-128">制限の値を指定する場合、文字列置換ではなく、パラメーター付きのクエリを使って、SQL への注入攻撃のリスクを最小限にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="96e2c-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96e2c-129">配列内の要素数は、指定したスキーマ コレクションでサポートされる制限数以下にする必要があります。そうでない場合、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="96e2c-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="96e2c-130">制限は最大数よりも小さい場合があります。</span><span class="sxs-lookup"><span data-stu-id="96e2c-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="96e2c-131">指定されていない制限は、null (無制限) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="96e2c-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="96e2c-132">呼び出すことによってサポートされている制限の一覧を特定の .NET Framework マネージ プロバイダーを照会することができます、 **GetSchema** "Restrictions"は、制限のスキーマ コレクションの名前を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="96e2c-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="96e2c-133">これにより、コレクション名の一覧、制限の名前、既定の制限値、および制限の番号と共に、<xref:System.Data.DataTable> が返されます。</span><span class="sxs-lookup"><span data-stu-id="96e2c-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="96e2c-134">例</span><span class="sxs-lookup"><span data-stu-id="96e2c-134">Example</span></span>  
 <span data-ttu-id="96e2c-135">次の例を使用する方法を示します、<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>の .NET Framework Data Provider for SQL Server メソッド<xref:System.Data.SqlClient.SqlConnection>に関する、すべてのテーブルに含まれているスキーマ情報を取得するクラス、 **AdventureWorks**サンプル データベース、および"Sales"スキーマ内のテーブルのみに返される情報を制限します。</span><span class="sxs-lookup"><span data-stu-id="96e2c-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="96e2c-136">SQL Server スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="96e2c-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="96e2c-137">次の表に、SQL Server スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="96e2c-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="96e2c-138">Users</span><span class="sxs-lookup"><span data-stu-id="96e2c-138">Users</span></span>  
  
|<span data-ttu-id="96e2c-139">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-139">Restriction Name</span></span>|<span data-ttu-id="96e2c-140">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-140">Parameter Name</span></span>|<span data-ttu-id="96e2c-141">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-141">Restriction Default</span></span>|<span data-ttu-id="96e2c-142">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="96e2c-143">User_Name</span></span>|@Name|<span data-ttu-id="96e2c-144">name</span><span class="sxs-lookup"><span data-stu-id="96e2c-144">name</span></span>|<span data-ttu-id="96e2c-145">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="96e2c-146">Databases</span><span class="sxs-lookup"><span data-stu-id="96e2c-146">Databases</span></span>  
  
|<span data-ttu-id="96e2c-147">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-147">Restriction Name</span></span>|<span data-ttu-id="96e2c-148">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-148">Parameter Name</span></span>|<span data-ttu-id="96e2c-149">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-149">Restriction Default</span></span>|<span data-ttu-id="96e2c-150">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-151">name</span><span class="sxs-lookup"><span data-stu-id="96e2c-151">Name</span></span>|@Name|<span data-ttu-id="96e2c-152">name</span><span class="sxs-lookup"><span data-stu-id="96e2c-152">Name</span></span>|<span data-ttu-id="96e2c-153">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="96e2c-154">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="96e2c-154">Tables</span></span>  
  
|<span data-ttu-id="96e2c-155">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-155">Restriction Name</span></span>|<span data-ttu-id="96e2c-156">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-156">Parameter Name</span></span>|<span data-ttu-id="96e2c-157">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-157">Restriction Default</span></span>|<span data-ttu-id="96e2c-158">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-159">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-160">TABLE_CATALOG</span></span>|<span data-ttu-id="96e2c-161">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-161">1</span></span>|  
|<span data-ttu-id="96e2c-162">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-162">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="96e2c-164">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-164">2</span></span>|  
|<span data-ttu-id="96e2c-165">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-165">Table</span></span>|@Name|<span data-ttu-id="96e2c-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-166">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-167">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-167">3</span></span>|  
|<span data-ttu-id="96e2c-168">TableType</span><span class="sxs-lookup"><span data-stu-id="96e2c-168">TableType</span></span>|@TableType|<span data-ttu-id="96e2c-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="96e2c-169">TABLE_TYPE</span></span>|<span data-ttu-id="96e2c-170">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="96e2c-171">列</span><span class="sxs-lookup"><span data-stu-id="96e2c-171">Columns</span></span>  
  
|<span data-ttu-id="96e2c-172">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-172">Restriction Name</span></span>|<span data-ttu-id="96e2c-173">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-173">Parameter Name</span></span>|<span data-ttu-id="96e2c-174">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-174">Restriction Default</span></span>|<span data-ttu-id="96e2c-175">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-176">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-177">TABLE_CATALOG</span></span>|<span data-ttu-id="96e2c-178">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-178">1</span></span>|  
|<span data-ttu-id="96e2c-179">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-179">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="96e2c-181">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-181">2</span></span>|  
|<span data-ttu-id="96e2c-182">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-182">Table</span></span>|@Table|<span data-ttu-id="96e2c-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-183">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-184">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-184">3</span></span>|  
|<span data-ttu-id="96e2c-185">Column</span><span class="sxs-lookup"><span data-stu-id="96e2c-185">Column</span></span>|@Column|<span data-ttu-id="96e2c-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-186">COLUMN_NAME</span></span>|<span data-ttu-id="96e2c-187">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="96e2c-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="96e2c-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="96e2c-189">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-189">Restriction Name</span></span>|<span data-ttu-id="96e2c-190">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-190">Parameter Name</span></span>|<span data-ttu-id="96e2c-191">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-191">Restriction Default</span></span>|<span data-ttu-id="96e2c-192">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-193">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-194">TABLE_CATALOG</span></span>|<span data-ttu-id="96e2c-195">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-195">1</span></span>|  
|<span data-ttu-id="96e2c-196">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-196">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="96e2c-198">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-198">2</span></span>|  
|<span data-ttu-id="96e2c-199">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-199">Table</span></span>|@Table|<span data-ttu-id="96e2c-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-200">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-201">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-201">3</span></span>|  
|<span data-ttu-id="96e2c-202">Column</span><span class="sxs-lookup"><span data-stu-id="96e2c-202">Column</span></span>|@Column|<span data-ttu-id="96e2c-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-203">COLUMN_NAME</span></span>|<span data-ttu-id="96e2c-204">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="96e2c-205">ビュー</span><span class="sxs-lookup"><span data-stu-id="96e2c-205">Views</span></span>  
  
|<span data-ttu-id="96e2c-206">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-206">Restriction Name</span></span>|<span data-ttu-id="96e2c-207">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-207">Parameter Name</span></span>|<span data-ttu-id="96e2c-208">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-208">Restriction Default</span></span>|<span data-ttu-id="96e2c-209">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-210">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-211">TABLE_CATALOG</span></span>|<span data-ttu-id="96e2c-212">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-212">1</span></span>|  
|<span data-ttu-id="96e2c-213">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-213">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="96e2c-215">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-215">2</span></span>|  
|<span data-ttu-id="96e2c-216">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-216">Table</span></span>|@Table|<span data-ttu-id="96e2c-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-217">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-218">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="96e2c-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="96e2c-219">ViewColumns</span></span>  
  
|<span data-ttu-id="96e2c-220">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-220">Restriction Name</span></span>|<span data-ttu-id="96e2c-221">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-221">Parameter Name</span></span>|<span data-ttu-id="96e2c-222">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-222">Restriction Default</span></span>|<span data-ttu-id="96e2c-223">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-224">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-225">VIEW_CATALOG</span></span>|<span data-ttu-id="96e2c-226">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-226">1</span></span>|  
|<span data-ttu-id="96e2c-227">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-227">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="96e2c-229">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-229">2</span></span>|  
|<span data-ttu-id="96e2c-230">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-230">Table</span></span>|@Table|<span data-ttu-id="96e2c-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-231">VIEW_NAME</span></span>|<span data-ttu-id="96e2c-232">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-232">3</span></span>|  
|<span data-ttu-id="96e2c-233">Column</span><span class="sxs-lookup"><span data-stu-id="96e2c-233">Column</span></span>|@Column|<span data-ttu-id="96e2c-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-234">COLUMN_NAME</span></span>|<span data-ttu-id="96e2c-235">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="96e2c-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="96e2c-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="96e2c-237">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-237">Restriction Name</span></span>|<span data-ttu-id="96e2c-238">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-238">Parameter Name</span></span>|<span data-ttu-id="96e2c-239">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-239">Restriction Default</span></span>|<span data-ttu-id="96e2c-240">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-241">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="96e2c-243">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-243">1</span></span>|  
|<span data-ttu-id="96e2c-244">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-244">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="96e2c-246">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-246">2</span></span>|  
|<span data-ttu-id="96e2c-247">name</span><span class="sxs-lookup"><span data-stu-id="96e2c-247">Name</span></span>|@Name|<span data-ttu-id="96e2c-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="96e2c-249">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-249">3</span></span>|  
|<span data-ttu-id="96e2c-250">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96e2c-250">Parameter</span></span>|@Parameter|<span data-ttu-id="96e2c-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-251">PARAMETER_NAME</span></span>|<span data-ttu-id="96e2c-252">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="96e2c-253">手順</span><span class="sxs-lookup"><span data-stu-id="96e2c-253">Procedures</span></span>  
  
|<span data-ttu-id="96e2c-254">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-254">Restriction Name</span></span>|<span data-ttu-id="96e2c-255">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-255">Parameter Name</span></span>|<span data-ttu-id="96e2c-256">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-256">Restriction Default</span></span>|<span data-ttu-id="96e2c-257">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-258">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="96e2c-260">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-260">1</span></span>|  
|<span data-ttu-id="96e2c-261">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-261">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="96e2c-263">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-263">2</span></span>|  
|<span data-ttu-id="96e2c-264">name</span><span class="sxs-lookup"><span data-stu-id="96e2c-264">Name</span></span>|@Name|<span data-ttu-id="96e2c-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="96e2c-266">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-266">3</span></span>|  
|<span data-ttu-id="96e2c-267">型</span><span class="sxs-lookup"><span data-stu-id="96e2c-267">Type</span></span>|@Type|<span data-ttu-id="96e2c-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="96e2c-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="96e2c-269">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="96e2c-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="96e2c-270">IndexColumns</span></span>  
  
|<span data-ttu-id="96e2c-271">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-271">Restriction Name</span></span>|<span data-ttu-id="96e2c-272">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-272">Parameter Name</span></span>|<span data-ttu-id="96e2c-273">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-273">Restriction Default</span></span>|<span data-ttu-id="96e2c-274">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-275">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="96e2c-276">db_name()</span></span>|<span data-ttu-id="96e2c-277">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-277">1</span></span>|  
|<span data-ttu-id="96e2c-278">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-278">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="96e2c-279">user_name()</span></span>|<span data-ttu-id="96e2c-280">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-280">2</span></span>|  
|<span data-ttu-id="96e2c-281">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-281">Table</span></span>|@Table|<span data-ttu-id="96e2c-282">o.name</span><span class="sxs-lookup"><span data-stu-id="96e2c-282">o.name</span></span>|<span data-ttu-id="96e2c-283">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-283">3</span></span>|  
|<span data-ttu-id="96e2c-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="96e2c-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="96e2c-285">x.name</span><span class="sxs-lookup"><span data-stu-id="96e2c-285">x.name</span></span>|<span data-ttu-id="96e2c-286">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-286">4</span></span>|  
|<span data-ttu-id="96e2c-287">Column</span><span class="sxs-lookup"><span data-stu-id="96e2c-287">Column</span></span>|@Column|<span data-ttu-id="96e2c-288">c.name</span><span class="sxs-lookup"><span data-stu-id="96e2c-288">c.name</span></span>|<span data-ttu-id="96e2c-289">5</span><span class="sxs-lookup"><span data-stu-id="96e2c-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="96e2c-290">Indexes</span><span class="sxs-lookup"><span data-stu-id="96e2c-290">Indexes</span></span>  
  
|<span data-ttu-id="96e2c-291">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-291">Restriction Name</span></span>|<span data-ttu-id="96e2c-292">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-292">Parameter Name</span></span>|<span data-ttu-id="96e2c-293">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-293">Restriction Default</span></span>|<span data-ttu-id="96e2c-294">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-295">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="96e2c-296">db_name()</span></span>|<span data-ttu-id="96e2c-297">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-297">1</span></span>|  
|<span data-ttu-id="96e2c-298">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-298">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="96e2c-299">user_name()</span></span>|<span data-ttu-id="96e2c-300">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-300">2</span></span>|  
|<span data-ttu-id="96e2c-301">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-301">Table</span></span>|@Table|<span data-ttu-id="96e2c-302">o.name</span><span class="sxs-lookup"><span data-stu-id="96e2c-302">o.name</span></span>|<span data-ttu-id="96e2c-303">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="96e2c-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="96e2c-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="96e2c-305">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-305">Restriction Name</span></span>|<span data-ttu-id="96e2c-306">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-306">Parameter Name</span></span>|<span data-ttu-id="96e2c-307">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-307">Restriction Default</span></span>|<span data-ttu-id="96e2c-308">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="96e2c-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="96e2c-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="96e2c-310">assemblies.name</span></span>|<span data-ttu-id="96e2c-311">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-311">1</span></span>|  
|<span data-ttu-id="96e2c-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="96e2c-312">udt_name</span></span>|@UDTName|<span data-ttu-id="96e2c-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="96e2c-313">types.assembly_class</span></span>|<span data-ttu-id="96e2c-314">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="96e2c-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="96e2c-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="96e2c-316">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-316">Restriction Name</span></span>|<span data-ttu-id="96e2c-317">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-317">Parameter Name</span></span>|<span data-ttu-id="96e2c-318">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-318">Restriction Default</span></span>|<span data-ttu-id="96e2c-319">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-320">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="96e2c-322">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-322">1</span></span>|  
|<span data-ttu-id="96e2c-323">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-323">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="96e2c-325">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-325">2</span></span>|  
|<span data-ttu-id="96e2c-326">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-326">Table</span></span>|@Table|<span data-ttu-id="96e2c-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-327">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-328">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-328">3</span></span>|  
|<span data-ttu-id="96e2c-329">name</span><span class="sxs-lookup"><span data-stu-id="96e2c-329">Name</span></span>|@Name|<span data-ttu-id="96e2c-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="96e2c-331">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="96e2c-332">SQL Server 2008 スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="96e2c-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="96e2c-333">次の表に、SQL Server 2008 スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="96e2c-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="96e2c-334">これらの制限は、.NET Framework 3.5 SP1 および SQL Server 2008 以降で有効です。</span><span class="sxs-lookup"><span data-stu-id="96e2c-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="96e2c-335">これらの制限は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="96e2c-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="96e2c-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="96e2c-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="96e2c-337">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-337">Restriction Name</span></span>|<span data-ttu-id="96e2c-338">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-338">Parameter Name</span></span>|<span data-ttu-id="96e2c-339">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-339">Restriction Default</span></span>|<span data-ttu-id="96e2c-340">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-341">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-342">TABLE_CATALOG</span></span>|<span data-ttu-id="96e2c-343">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-343">1</span></span>|  
|<span data-ttu-id="96e2c-344">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-344">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="96e2c-346">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-346">2</span></span>|  
|<span data-ttu-id="96e2c-347">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-347">Table</span></span>|@Table|<span data-ttu-id="96e2c-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-348">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-349">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="96e2c-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="96e2c-350">AllColumns</span></span>  
  
|<span data-ttu-id="96e2c-351">制限の名前</span><span class="sxs-lookup"><span data-stu-id="96e2c-351">Restriction Name</span></span>|<span data-ttu-id="96e2c-352">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="96e2c-352">Parameter Name</span></span>|<span data-ttu-id="96e2c-353">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="96e2c-353">Restriction Default</span></span>|<span data-ttu-id="96e2c-354">制限の番号</span><span class="sxs-lookup"><span data-stu-id="96e2c-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="96e2c-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="96e2c-355">Catalog</span></span>|@Catalog|<span data-ttu-id="96e2c-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="96e2c-356">TABLE_CATALOG</span></span>|<span data-ttu-id="96e2c-357">1</span><span class="sxs-lookup"><span data-stu-id="96e2c-357">1</span></span>|  
|<span data-ttu-id="96e2c-358">Owner</span><span class="sxs-lookup"><span data-stu-id="96e2c-358">Owner</span></span>|@Owner|<span data-ttu-id="96e2c-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="96e2c-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="96e2c-360">2</span><span class="sxs-lookup"><span data-stu-id="96e2c-360">2</span></span>|  
|<span data-ttu-id="96e2c-361">テーブル</span><span class="sxs-lookup"><span data-stu-id="96e2c-361">Table</span></span>|@Table|<span data-ttu-id="96e2c-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-362">TABLE_NAME</span></span>|<span data-ttu-id="96e2c-363">3</span><span class="sxs-lookup"><span data-stu-id="96e2c-363">3</span></span>|  
|<span data-ttu-id="96e2c-364">Column</span><span class="sxs-lookup"><span data-stu-id="96e2c-364">Column</span></span>|@Column|<span data-ttu-id="96e2c-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="96e2c-365">COLUMN_NAME</span></span>|<span data-ttu-id="96e2c-366">4</span><span class="sxs-lookup"><span data-stu-id="96e2c-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96e2c-367">参照</span><span class="sxs-lookup"><span data-stu-id="96e2c-367">See Also</span></span>  
 [<span data-ttu-id="96e2c-368">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="96e2c-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
