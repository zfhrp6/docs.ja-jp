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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4a3cc1f0c27af1ad41e14374b4c155e6b8620f28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="schema-restrictions"></a><span data-ttu-id="24268-102">スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="24268-102">Schema Restrictions</span></span>
<span data-ttu-id="24268-103">2 番目の省略可能なパラメーター、 **GetSchema**メソッドは、スキーマ情報の量を制限するために使用される制限が返されに渡される、 **GetSchema**文字列の配列としてメソッド.</span><span class="sxs-lookup"><span data-stu-id="24268-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="24268-104">配列での位置により、渡すことができる値が決定します。これは、制限の番号に相当します。</span><span class="sxs-lookup"><span data-stu-id="24268-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="24268-105">たとえば、次の表は、.NET Framework Data Provider for SQL Server を使用して、"Tables" スキーマ コレクションによりサポートされる制限を示しています。</span><span class="sxs-lookup"><span data-stu-id="24268-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="24268-106">SQL Server スキーマ コレクションの追加の制限をこのトピックの終わりに示します。</span><span class="sxs-lookup"><span data-stu-id="24268-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="24268-107">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-107">Restriction Name</span></span>|<span data-ttu-id="24268-108">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-108">Parameter Name</span></span>|<span data-ttu-id="24268-109">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-109">Restriction Default</span></span>|<span data-ttu-id="24268-110">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-111">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-112">TABLE_CATALOG</span></span>|<span data-ttu-id="24268-113">1</span><span class="sxs-lookup"><span data-stu-id="24268-113">1</span></span>|  
|<span data-ttu-id="24268-114">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-114">Owner</span></span>|@Owner|<span data-ttu-id="24268-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="24268-116">2</span><span class="sxs-lookup"><span data-stu-id="24268-116">2</span></span>|  
|<span data-ttu-id="24268-117">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-117">Table</span></span>|@Name|<span data-ttu-id="24268-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-118">TABLE_NAME</span></span>|<span data-ttu-id="24268-119">3</span><span class="sxs-lookup"><span data-stu-id="24268-119">3</span></span>|  
|<span data-ttu-id="24268-120">TableType</span><span class="sxs-lookup"><span data-stu-id="24268-120">TableType</span></span>|@TableType|<span data-ttu-id="24268-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24268-121">TABLE_TYPE</span></span>|<span data-ttu-id="24268-122">4</span><span class="sxs-lookup"><span data-stu-id="24268-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="24268-123">制限値の指定</span><span class="sxs-lookup"><span data-stu-id="24268-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="24268-124">"Tables" スキーマ コレクションの制限の 1 つを使用するには、4 つの要素を使って文字列の配列を作成してから、制限の番号と一致する要素内に値を配置します。</span><span class="sxs-lookup"><span data-stu-id="24268-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="24268-125">たとえば、テーブルを制限によって返される、 **GetSchema** "Sales"スキーマ内のテーブルのみをメソッドに渡す前に"Sales"に配列の 2 番目の要素を設定する、 **GetSchema**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="24268-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24268-126">`SqlClient` と `OracleClient` の制限のコレクションには、追加の `ParameterName` 列があります。</span><span class="sxs-lookup"><span data-stu-id="24268-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="24268-127">制限の既定の列は、下位互換性のために存在してはいますが、現在は無視されています。</span><span class="sxs-lookup"><span data-stu-id="24268-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="24268-128">制限の値を指定する場合、文字列置換ではなく、パラメーター付きのクエリを使って、SQL への注入攻撃のリスクを最小限にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="24268-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24268-129">配列内の要素数は、指定したスキーマ コレクションでサポートされる制限数以下にする必要があります。そうでない場合、<xref:System.ArgumentException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="24268-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="24268-130">制限は最大数よりも小さい場合があります。</span><span class="sxs-lookup"><span data-stu-id="24268-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="24268-131">指定されていない制限は、null (無制限) と見なされます。</span><span class="sxs-lookup"><span data-stu-id="24268-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="24268-132">呼び出すことによってサポートされている制限の一覧を特定の .NET Framework マネージ プロバイダーを照会することができます、 **GetSchema** "Restrictions"は、制限のスキーマ コレクションの名前を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="24268-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="24268-133">これにより、コレクション名の一覧、制限の名前、既定の制限値、および制限の番号と共に、<xref:System.Data.DataTable> が返されます。</span><span class="sxs-lookup"><span data-stu-id="24268-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="24268-134">例</span><span class="sxs-lookup"><span data-stu-id="24268-134">Example</span></span>  
 <span data-ttu-id="24268-135">次の例を使用する方法を示します、<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>の .NET Framework Data Provider for SQL Server メソッド<xref:System.Data.SqlClient.SqlConnection>に関する、すべてのテーブルに含まれているスキーマ情報を取得するクラス、 **AdventureWorks**サンプル データベース、および"Sales"スキーマ内のテーブルのみに返される情報を制限します。</span><span class="sxs-lookup"><span data-stu-id="24268-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="24268-136">SQL Server スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="24268-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="24268-137">次の表に、SQL Server スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="24268-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="24268-138">Users</span><span class="sxs-lookup"><span data-stu-id="24268-138">Users</span></span>  
  
|<span data-ttu-id="24268-139">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-139">Restriction Name</span></span>|<span data-ttu-id="24268-140">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-140">Parameter Name</span></span>|<span data-ttu-id="24268-141">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-141">Restriction Default</span></span>|<span data-ttu-id="24268-142">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="24268-143">User_Name</span></span>|@Name|<span data-ttu-id="24268-144">name</span><span class="sxs-lookup"><span data-stu-id="24268-144">name</span></span>|<span data-ttu-id="24268-145">1</span><span class="sxs-lookup"><span data-stu-id="24268-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="24268-146">Databases</span><span class="sxs-lookup"><span data-stu-id="24268-146">Databases</span></span>  
  
|<span data-ttu-id="24268-147">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-147">Restriction Name</span></span>|<span data-ttu-id="24268-148">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-148">Parameter Name</span></span>|<span data-ttu-id="24268-149">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-149">Restriction Default</span></span>|<span data-ttu-id="24268-150">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-151">name</span><span class="sxs-lookup"><span data-stu-id="24268-151">Name</span></span>|@Name|<span data-ttu-id="24268-152">name</span><span class="sxs-lookup"><span data-stu-id="24268-152">Name</span></span>|<span data-ttu-id="24268-153">1</span><span class="sxs-lookup"><span data-stu-id="24268-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="24268-154">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="24268-154">Tables</span></span>  
  
|<span data-ttu-id="24268-155">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-155">Restriction Name</span></span>|<span data-ttu-id="24268-156">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-156">Parameter Name</span></span>|<span data-ttu-id="24268-157">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-157">Restriction Default</span></span>|<span data-ttu-id="24268-158">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-159">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-160">TABLE_CATALOG</span></span>|<span data-ttu-id="24268-161">1</span><span class="sxs-lookup"><span data-stu-id="24268-161">1</span></span>|  
|<span data-ttu-id="24268-162">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-162">Owner</span></span>|@Owner|<span data-ttu-id="24268-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="24268-164">2</span><span class="sxs-lookup"><span data-stu-id="24268-164">2</span></span>|  
|<span data-ttu-id="24268-165">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-165">Table</span></span>|@Name|<span data-ttu-id="24268-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-166">TABLE_NAME</span></span>|<span data-ttu-id="24268-167">3</span><span class="sxs-lookup"><span data-stu-id="24268-167">3</span></span>|  
|<span data-ttu-id="24268-168">TableType</span><span class="sxs-lookup"><span data-stu-id="24268-168">TableType</span></span>|@TableType|<span data-ttu-id="24268-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24268-169">TABLE_TYPE</span></span>|<span data-ttu-id="24268-170">4</span><span class="sxs-lookup"><span data-stu-id="24268-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="24268-171">列</span><span class="sxs-lookup"><span data-stu-id="24268-171">Columns</span></span>  
  
|<span data-ttu-id="24268-172">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-172">Restriction Name</span></span>|<span data-ttu-id="24268-173">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-173">Parameter Name</span></span>|<span data-ttu-id="24268-174">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-174">Restriction Default</span></span>|<span data-ttu-id="24268-175">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-176">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-177">TABLE_CATALOG</span></span>|<span data-ttu-id="24268-178">1</span><span class="sxs-lookup"><span data-stu-id="24268-178">1</span></span>|  
|<span data-ttu-id="24268-179">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-179">Owner</span></span>|@Owner|<span data-ttu-id="24268-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="24268-181">2</span><span class="sxs-lookup"><span data-stu-id="24268-181">2</span></span>|  
|<span data-ttu-id="24268-182">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-182">Table</span></span>|@Table|<span data-ttu-id="24268-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-183">TABLE_NAME</span></span>|<span data-ttu-id="24268-184">3</span><span class="sxs-lookup"><span data-stu-id="24268-184">3</span></span>|  
|<span data-ttu-id="24268-185">Column</span><span class="sxs-lookup"><span data-stu-id="24268-185">Column</span></span>|@Column|<span data-ttu-id="24268-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-186">COLUMN_NAME</span></span>|<span data-ttu-id="24268-187">4</span><span class="sxs-lookup"><span data-stu-id="24268-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="24268-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="24268-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="24268-189">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-189">Restriction Name</span></span>|<span data-ttu-id="24268-190">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-190">Parameter Name</span></span>|<span data-ttu-id="24268-191">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-191">Restriction Default</span></span>|<span data-ttu-id="24268-192">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-193">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-194">TABLE_CATALOG</span></span>|<span data-ttu-id="24268-195">1</span><span class="sxs-lookup"><span data-stu-id="24268-195">1</span></span>|  
|<span data-ttu-id="24268-196">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-196">Owner</span></span>|@Owner|<span data-ttu-id="24268-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="24268-198">2</span><span class="sxs-lookup"><span data-stu-id="24268-198">2</span></span>|  
|<span data-ttu-id="24268-199">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-199">Table</span></span>|@Table|<span data-ttu-id="24268-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-200">TABLE_NAME</span></span>|<span data-ttu-id="24268-201">3</span><span class="sxs-lookup"><span data-stu-id="24268-201">3</span></span>|  
|<span data-ttu-id="24268-202">Column</span><span class="sxs-lookup"><span data-stu-id="24268-202">Column</span></span>|@Column|<span data-ttu-id="24268-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-203">COLUMN_NAME</span></span>|<span data-ttu-id="24268-204">4</span><span class="sxs-lookup"><span data-stu-id="24268-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="24268-205">ビュー</span><span class="sxs-lookup"><span data-stu-id="24268-205">Views</span></span>  
  
|<span data-ttu-id="24268-206">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-206">Restriction Name</span></span>|<span data-ttu-id="24268-207">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-207">Parameter Name</span></span>|<span data-ttu-id="24268-208">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-208">Restriction Default</span></span>|<span data-ttu-id="24268-209">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-210">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-211">TABLE_CATALOG</span></span>|<span data-ttu-id="24268-212">1</span><span class="sxs-lookup"><span data-stu-id="24268-212">1</span></span>|  
|<span data-ttu-id="24268-213">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-213">Owner</span></span>|@Owner|<span data-ttu-id="24268-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="24268-215">2</span><span class="sxs-lookup"><span data-stu-id="24268-215">2</span></span>|  
|<span data-ttu-id="24268-216">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-216">Table</span></span>|@Table|<span data-ttu-id="24268-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-217">TABLE_NAME</span></span>|<span data-ttu-id="24268-218">3</span><span class="sxs-lookup"><span data-stu-id="24268-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="24268-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="24268-219">ViewColumns</span></span>  
  
|<span data-ttu-id="24268-220">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-220">Restriction Name</span></span>|<span data-ttu-id="24268-221">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-221">Parameter Name</span></span>|<span data-ttu-id="24268-222">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-222">Restriction Default</span></span>|<span data-ttu-id="24268-223">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-224">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-225">VIEW_CATALOG</span></span>|<span data-ttu-id="24268-226">1</span><span class="sxs-lookup"><span data-stu-id="24268-226">1</span></span>|  
|<span data-ttu-id="24268-227">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-227">Owner</span></span>|@Owner|<span data-ttu-id="24268-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="24268-229">2</span><span class="sxs-lookup"><span data-stu-id="24268-229">2</span></span>|  
|<span data-ttu-id="24268-230">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-230">Table</span></span>|@Table|<span data-ttu-id="24268-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-231">VIEW_NAME</span></span>|<span data-ttu-id="24268-232">3</span><span class="sxs-lookup"><span data-stu-id="24268-232">3</span></span>|  
|<span data-ttu-id="24268-233">Column</span><span class="sxs-lookup"><span data-stu-id="24268-233">Column</span></span>|@Column|<span data-ttu-id="24268-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-234">COLUMN_NAME</span></span>|<span data-ttu-id="24268-235">4</span><span class="sxs-lookup"><span data-stu-id="24268-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="24268-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="24268-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="24268-237">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-237">Restriction Name</span></span>|<span data-ttu-id="24268-238">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-238">Parameter Name</span></span>|<span data-ttu-id="24268-239">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-239">Restriction Default</span></span>|<span data-ttu-id="24268-240">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-241">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="24268-243">1</span><span class="sxs-lookup"><span data-stu-id="24268-243">1</span></span>|  
|<span data-ttu-id="24268-244">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-244">Owner</span></span>|@Owner|<span data-ttu-id="24268-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="24268-246">2</span><span class="sxs-lookup"><span data-stu-id="24268-246">2</span></span>|  
|<span data-ttu-id="24268-247">name</span><span class="sxs-lookup"><span data-stu-id="24268-247">Name</span></span>|@Name|<span data-ttu-id="24268-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="24268-249">3</span><span class="sxs-lookup"><span data-stu-id="24268-249">3</span></span>|  
|<span data-ttu-id="24268-250">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24268-250">Parameter</span></span>|@Parameter|<span data-ttu-id="24268-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-251">PARAMETER_NAME</span></span>|<span data-ttu-id="24268-252">4</span><span class="sxs-lookup"><span data-stu-id="24268-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="24268-253">手順</span><span class="sxs-lookup"><span data-stu-id="24268-253">Procedures</span></span>  
  
|<span data-ttu-id="24268-254">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-254">Restriction Name</span></span>|<span data-ttu-id="24268-255">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-255">Parameter Name</span></span>|<span data-ttu-id="24268-256">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-256">Restriction Default</span></span>|<span data-ttu-id="24268-257">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-258">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="24268-260">1</span><span class="sxs-lookup"><span data-stu-id="24268-260">1</span></span>|  
|<span data-ttu-id="24268-261">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-261">Owner</span></span>|@Owner|<span data-ttu-id="24268-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="24268-263">2</span><span class="sxs-lookup"><span data-stu-id="24268-263">2</span></span>|  
|<span data-ttu-id="24268-264">name</span><span class="sxs-lookup"><span data-stu-id="24268-264">Name</span></span>|@Name|<span data-ttu-id="24268-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="24268-266">3</span><span class="sxs-lookup"><span data-stu-id="24268-266">3</span></span>|  
|<span data-ttu-id="24268-267">型</span><span class="sxs-lookup"><span data-stu-id="24268-267">Type</span></span>|@Type|<span data-ttu-id="24268-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24268-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="24268-269">4</span><span class="sxs-lookup"><span data-stu-id="24268-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="24268-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="24268-270">IndexColumns</span></span>  
  
|<span data-ttu-id="24268-271">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-271">Restriction Name</span></span>|<span data-ttu-id="24268-272">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-272">Parameter Name</span></span>|<span data-ttu-id="24268-273">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-273">Restriction Default</span></span>|<span data-ttu-id="24268-274">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-275">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="24268-276">db_name()</span></span>|<span data-ttu-id="24268-277">1</span><span class="sxs-lookup"><span data-stu-id="24268-277">1</span></span>|  
|<span data-ttu-id="24268-278">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-278">Owner</span></span>|@Owner|<span data-ttu-id="24268-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="24268-279">user_name()</span></span>|<span data-ttu-id="24268-280">2</span><span class="sxs-lookup"><span data-stu-id="24268-280">2</span></span>|  
|<span data-ttu-id="24268-281">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-281">Table</span></span>|@Table|<span data-ttu-id="24268-282">o.name</span><span class="sxs-lookup"><span data-stu-id="24268-282">o.name</span></span>|<span data-ttu-id="24268-283">3</span><span class="sxs-lookup"><span data-stu-id="24268-283">3</span></span>|  
|<span data-ttu-id="24268-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="24268-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="24268-285">x.name</span><span class="sxs-lookup"><span data-stu-id="24268-285">x.name</span></span>|<span data-ttu-id="24268-286">4</span><span class="sxs-lookup"><span data-stu-id="24268-286">4</span></span>|  
|<span data-ttu-id="24268-287">Column</span><span class="sxs-lookup"><span data-stu-id="24268-287">Column</span></span>|@Column|<span data-ttu-id="24268-288">c.name</span><span class="sxs-lookup"><span data-stu-id="24268-288">c.name</span></span>|<span data-ttu-id="24268-289">5</span><span class="sxs-lookup"><span data-stu-id="24268-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="24268-290">Indexes</span><span class="sxs-lookup"><span data-stu-id="24268-290">Indexes</span></span>  
  
|<span data-ttu-id="24268-291">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-291">Restriction Name</span></span>|<span data-ttu-id="24268-292">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-292">Parameter Name</span></span>|<span data-ttu-id="24268-293">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-293">Restriction Default</span></span>|<span data-ttu-id="24268-294">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-295">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="24268-296">db_name()</span></span>|<span data-ttu-id="24268-297">1</span><span class="sxs-lookup"><span data-stu-id="24268-297">1</span></span>|  
|<span data-ttu-id="24268-298">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-298">Owner</span></span>|@Owner|<span data-ttu-id="24268-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="24268-299">user_name()</span></span>|<span data-ttu-id="24268-300">2</span><span class="sxs-lookup"><span data-stu-id="24268-300">2</span></span>|  
|<span data-ttu-id="24268-301">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-301">Table</span></span>|@Table|<span data-ttu-id="24268-302">o.name</span><span class="sxs-lookup"><span data-stu-id="24268-302">o.name</span></span>|<span data-ttu-id="24268-303">3</span><span class="sxs-lookup"><span data-stu-id="24268-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="24268-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="24268-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="24268-305">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-305">Restriction Name</span></span>|<span data-ttu-id="24268-306">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-306">Parameter Name</span></span>|<span data-ttu-id="24268-307">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-307">Restriction Default</span></span>|<span data-ttu-id="24268-308">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="24268-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="24268-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="24268-310">assemblies.name</span></span>|<span data-ttu-id="24268-311">1</span><span class="sxs-lookup"><span data-stu-id="24268-311">1</span></span>|  
|<span data-ttu-id="24268-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="24268-312">udt_name</span></span>|@UDTName|<span data-ttu-id="24268-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="24268-313">types.assembly_class</span></span>|<span data-ttu-id="24268-314">2</span><span class="sxs-lookup"><span data-stu-id="24268-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="24268-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="24268-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="24268-316">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-316">Restriction Name</span></span>|<span data-ttu-id="24268-317">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-317">Parameter Name</span></span>|<span data-ttu-id="24268-318">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-318">Restriction Default</span></span>|<span data-ttu-id="24268-319">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-320">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="24268-322">1</span><span class="sxs-lookup"><span data-stu-id="24268-322">1</span></span>|  
|<span data-ttu-id="24268-323">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-323">Owner</span></span>|@Owner|<span data-ttu-id="24268-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="24268-325">2</span><span class="sxs-lookup"><span data-stu-id="24268-325">2</span></span>|  
|<span data-ttu-id="24268-326">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-326">Table</span></span>|@Table|<span data-ttu-id="24268-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-327">TABLE_NAME</span></span>|<span data-ttu-id="24268-328">3</span><span class="sxs-lookup"><span data-stu-id="24268-328">3</span></span>|  
|<span data-ttu-id="24268-329">name</span><span class="sxs-lookup"><span data-stu-id="24268-329">Name</span></span>|@Name|<span data-ttu-id="24268-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="24268-331">4</span><span class="sxs-lookup"><span data-stu-id="24268-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="24268-332">SQL Server 2008 スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="24268-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="24268-333">次の表に、SQL Server 2008 スキーマ コレクションの制限を示します。</span><span class="sxs-lookup"><span data-stu-id="24268-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="24268-334">これらの制限は、.NET Framework 3.5 SP1 および SQL Server 2008 以降で有効です。</span><span class="sxs-lookup"><span data-stu-id="24268-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="24268-335">これらの制限は、以前のバージョンの .NET Framework および SQL Server ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="24268-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="24268-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="24268-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="24268-337">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-337">Restriction Name</span></span>|<span data-ttu-id="24268-338">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-338">Parameter Name</span></span>|<span data-ttu-id="24268-339">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-339">Restriction Default</span></span>|<span data-ttu-id="24268-340">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-341">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-342">TABLE_CATALOG</span></span>|<span data-ttu-id="24268-343">1</span><span class="sxs-lookup"><span data-stu-id="24268-343">1</span></span>|  
|<span data-ttu-id="24268-344">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-344">Owner</span></span>|@Owner|<span data-ttu-id="24268-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="24268-346">2</span><span class="sxs-lookup"><span data-stu-id="24268-346">2</span></span>|  
|<span data-ttu-id="24268-347">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-347">Table</span></span>|@Table|<span data-ttu-id="24268-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-348">TABLE_NAME</span></span>|<span data-ttu-id="24268-349">3</span><span class="sxs-lookup"><span data-stu-id="24268-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="24268-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="24268-350">AllColumns</span></span>  
  
|<span data-ttu-id="24268-351">制限の名前</span><span class="sxs-lookup"><span data-stu-id="24268-351">Restriction Name</span></span>|<span data-ttu-id="24268-352">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="24268-352">Parameter Name</span></span>|<span data-ttu-id="24268-353">制限の既定値</span><span class="sxs-lookup"><span data-stu-id="24268-353">Restriction Default</span></span>|<span data-ttu-id="24268-354">制限の番号</span><span class="sxs-lookup"><span data-stu-id="24268-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="24268-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="24268-355">Catalog</span></span>|@Catalog|<span data-ttu-id="24268-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24268-356">TABLE_CATALOG</span></span>|<span data-ttu-id="24268-357">1</span><span class="sxs-lookup"><span data-stu-id="24268-357">1</span></span>|  
|<span data-ttu-id="24268-358">Owner</span><span class="sxs-lookup"><span data-stu-id="24268-358">Owner</span></span>|@Owner|<span data-ttu-id="24268-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24268-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="24268-360">2</span><span class="sxs-lookup"><span data-stu-id="24268-360">2</span></span>|  
|<span data-ttu-id="24268-361">テーブル</span><span class="sxs-lookup"><span data-stu-id="24268-361">Table</span></span>|@Table|<span data-ttu-id="24268-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-362">TABLE_NAME</span></span>|<span data-ttu-id="24268-363">3</span><span class="sxs-lookup"><span data-stu-id="24268-363">3</span></span>|  
|<span data-ttu-id="24268-364">Column</span><span class="sxs-lookup"><span data-stu-id="24268-364">Column</span></span>|@Column|<span data-ttu-id="24268-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24268-365">COLUMN_NAME</span></span>|<span data-ttu-id="24268-366">4</span><span class="sxs-lookup"><span data-stu-id="24268-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24268-367">参照</span><span class="sxs-lookup"><span data-stu-id="24268-367">See Also</span></span>  
 [<span data-ttu-id="24268-368">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="24268-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
