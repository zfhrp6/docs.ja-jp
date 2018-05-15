---
title: 行の検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 57ed6045ca0ea9f9579640839e8198716cf79fe0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="finding-rows"></a><span data-ttu-id="1450c-102">行の検索</span><span class="sxs-lookup"><span data-stu-id="1450c-102">Finding Rows</span></span>
<span data-ttu-id="1450c-103"><xref:System.Data.DataView.Find%2A> の <xref:System.Data.DataView.FindRows%2A> メソッドと <xref:System.Data.DataView> メソッドを使用すると、並べ替えキーの値に基づいて行を検索できます。</span><span class="sxs-lookup"><span data-stu-id="1450c-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="1450c-104">値が検索の大文字小文字の区別、**検索**と**FindRows**メソッドはによって決定されます、 **CaseSensitive** 、基になるプロパティ<xref:System.Data.DataTable>です。</span><span class="sxs-lookup"><span data-stu-id="1450c-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1450c-105">検索結果を返すには、検索値が既存の並べ替えキーの値と完全に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1450c-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="1450c-106">**検索**メソッドのインデックスを持つ整数を返します、<xref:System.Data.DataRowView>検索条件に一致します。</span><span class="sxs-lookup"><span data-stu-id="1450c-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="1450c-107">複数の行には、検索条件、一致した最初のインデックスのみが一致する場合**DataRowView**が返されます。</span><span class="sxs-lookup"><span data-stu-id="1450c-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="1450c-108">一致が見つからない場合**検索**-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="1450c-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="1450c-109">複数の行に一致する検索結果を返すを使用して、 **FindRows**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1450c-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="1450c-110">**FindRows**同様の機能、**検索**メソッドを返します点を除いて、 **DataRowView**配列内のすべての一致する行を参照する、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="1450c-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="1450c-111">一致が見つからない場合、 **DataRowView**配列は空になります。</span><span class="sxs-lookup"><span data-stu-id="1450c-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="1450c-112">使用する、**検索**または**FindRows**並べ替え順を指定する必要がありますメソッドで設定するか注文**ApplyDefaultSort**に**true**またはを使用して、**並べ替え**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="1450c-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="1450c-113">並べ替え順序が指定されないと、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="1450c-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="1450c-114">**検索**と**FindRows**メソッドがの長さが並べ替え順序で列の数と一致する入力として値の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="1450c-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="1450c-115">1 つの列に基づく並べ替えの場合は、1 つの値を渡します。</span><span class="sxs-lookup"><span data-stu-id="1450c-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="1450c-116">複数列に基づく並べ替えの場合は、オブジェクトの配列を渡します。</span><span class="sxs-lookup"><span data-stu-id="1450c-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="1450c-117">複数の列で並べ替えには、オブジェクトの配列内の値と一致するがで指定された列の順序に注意してください、**並べ替え**のプロパティ、 **DataView**です。</span><span class="sxs-lookup"><span data-stu-id="1450c-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="1450c-118">次のコード例は、**検索**メソッドに対して呼び出されると、 **DataView** 1 つの列の並べ替え順序を持つ。</span><span class="sxs-lookup"><span data-stu-id="1450c-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="1450c-119">場合、**並べ替え**プロパティが複数の列を指定します、によって指定された順序で各列に対して検索値を持つオブジェクトの配列を渡す必要があります、**並べ替え**プロパティは、次のコード例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="1450c-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="1450c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1450c-120">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="1450c-121">DataViews</span><span class="sxs-lookup"><span data-stu-id="1450c-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="1450c-122">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="1450c-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
