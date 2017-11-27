---
title: "型指定された DataSet の注釈"
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
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d3965ced44bae21feef3d01d49149387fce4fa46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="d5b18-102">型指定された DataSet の注釈</span><span class="sxs-lookup"><span data-stu-id="d5b18-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="d5b18-103">注釈を使用すると、基になるスキーマを変更せずに型指定された <xref:System.Data.DataSet> の要素の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d5b18-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="d5b18-104">基になるスキーマの要素の名前を修正するは、型指定された**データセット**にはないデータ ソースに存在だけでなく、データ ソース内に存在しているオブジェクトへの参照が失われるオブジェクトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5b18-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="d5b18-105">注釈を使用して、カスタマイズできますオブジェクトの名前、型指定された**データセット**、わかりやすい名前を持つを行うコードが読みやすく、型指定された**データセット**を維持したまま、使用するクライアントを簡単に基になるスキーマがそのままです。</span><span class="sxs-lookup"><span data-stu-id="d5b18-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="d5b18-106">次の schema 要素など、**顧客**のテーブル、 **Northwind**データベースになります、 **DataRow**のオブジェクト名**CustomersRow**と<xref:System.Data.DataRowCollection>という**顧客**です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="d5b18-107">A **DataRowCollection**の名前**顧客**クライアント コードで意味を持つが、 **DataRow**名前**CustomersRow**誤解を招き1 つのオブジェクトであるため</span><span class="sxs-lookup"><span data-stu-id="d5b18-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="d5b18-108">また、共通のシナリオでは、オブジェクトがせずに参照、**行**識別子代わりに、単に呼ばれることと、**顧客**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5b18-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="d5b18-109">解決、スキーマに注釈を付けるし、新しい名前を指定するには、 **DataRow**と**DataRowCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5b18-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="d5b18-110">上記のスキーマに注釈を付けたスキーマを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5b18-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="d5b18-111">指定する、 **typedName**の値**顧客**になります、 **DataRow**のオブジェクト名**顧客**です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="d5b18-112">指定する、 **typedPlural**の値**顧客**が保持されます、 **DataRowCollection**名前**顧客**です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="d5b18-113">使用できる注釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d5b18-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="d5b18-114">注釈</span><span class="sxs-lookup"><span data-stu-id="d5b18-114">Annotation</span></span>|<span data-ttu-id="d5b18-115">説明</span><span class="sxs-lookup"><span data-stu-id="d5b18-115">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d5b18-116">**typedName**</span><span class="sxs-lookup"><span data-stu-id="d5b18-116">**typedName**</span></span>|<span data-ttu-id="d5b18-117">オブジェクト名。</span><span class="sxs-lookup"><span data-stu-id="d5b18-117">Name of the object.</span></span>|  
|<span data-ttu-id="d5b18-118">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="d5b18-118">**typedPlural**</span></span>|<span data-ttu-id="d5b18-119">オブジェクトのコレクション名。</span><span class="sxs-lookup"><span data-stu-id="d5b18-119">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="d5b18-120">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="d5b18-120">**typedParent**</span></span>|<span data-ttu-id="d5b18-121">親のリレーションシップで参照される場合のオブジェクト名。</span><span class="sxs-lookup"><span data-stu-id="d5b18-121">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="d5b18-122">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="d5b18-122">**typedChildren**</span></span>|<span data-ttu-id="d5b18-123">子のリレーションシップからオブジェクトを返すメソッド名。</span><span class="sxs-lookup"><span data-stu-id="d5b18-123">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="d5b18-124">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="d5b18-124">**nullValue**</span></span>|<span data-ttu-id="d5b18-125">値の場合は、基になる値は**DBNull**です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="d5b18-126">次の表を参照してください**nullValue**注釈。</span><span class="sxs-lookup"><span data-stu-id="d5b18-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="d5b18-127">既定値は**_throw**です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="d5b18-128">次の表は、値を指定できる、 **nullValue**注釈。</span><span class="sxs-lookup"><span data-stu-id="d5b18-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="d5b18-129">nullValue の値</span><span class="sxs-lookup"><span data-stu-id="d5b18-129">nullValue Value</span></span>|<span data-ttu-id="d5b18-130">説明</span><span class="sxs-lookup"><span data-stu-id="d5b18-130">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="d5b18-131">*置換値*</span><span class="sxs-lookup"><span data-stu-id="d5b18-131">*Replacement Value*</span></span>|<span data-ttu-id="d5b18-132">返される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5b18-132">Specify a value to be returned.</span></span> <span data-ttu-id="d5b18-133">返された値は要素の型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5b18-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="d5b18-134">たとえば、整数型フィールドが null の場合に 0 を返すために `nullValue="0"` を使用します。</span><span class="sxs-lookup"><span data-stu-id="d5b18-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="d5b18-135">**_throw**</span><span class="sxs-lookup"><span data-stu-id="d5b18-135">**_throw**</span></span>|<span data-ttu-id="d5b18-136">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d5b18-136">Throw an exception.</span></span> <span data-ttu-id="d5b18-137">既定値です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-137">This is the default.</span></span>|  
|<span data-ttu-id="d5b18-138">**_null**</span><span class="sxs-lookup"><span data-stu-id="d5b18-138">**_null**</span></span>|<span data-ttu-id="d5b18-139">プリミティブ型が見つかった場合は、null 参照を返すか、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d5b18-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="d5b18-140">**_empty**</span><span class="sxs-lookup"><span data-stu-id="d5b18-140">**_empty**</span></span>|<span data-ttu-id="d5b18-141">文字列を返す**String.Empty**、それ以外の場合、空のコンス トラクターから作成されたオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="d5b18-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="d5b18-142">プリミティブ型が見つかった場合、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d5b18-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="d5b18-143">次の表は、型指定されたオブジェクトの既定値を示します**データセット**と使用可能な注釈です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="d5b18-144">オブジェクト/メソッド/イベント</span><span class="sxs-lookup"><span data-stu-id="d5b18-144">Object/Method/Event</span></span>|<span data-ttu-id="d5b18-145">既定値</span><span class="sxs-lookup"><span data-stu-id="d5b18-145">Default</span></span>|<span data-ttu-id="d5b18-146">注釈</span><span class="sxs-lookup"><span data-stu-id="d5b18-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="d5b18-147">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="d5b18-147">**DataTable**</span></span>|<span data-ttu-id="d5b18-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="d5b18-148">TableNameDataTable</span></span>|<span data-ttu-id="d5b18-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="d5b18-149">typedPlural</span></span>|  
|<span data-ttu-id="d5b18-150">**DataTable**メソッド</span><span class="sxs-lookup"><span data-stu-id="d5b18-150">**DataTable** Methods</span></span>|<span data-ttu-id="d5b18-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="d5b18-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="d5b18-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="d5b18-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="d5b18-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="d5b18-153">DeleteTableNameRow</span></span>|<span data-ttu-id="d5b18-154">typedName</span><span class="sxs-lookup"><span data-stu-id="d5b18-154">typedName</span></span>|  
|<span data-ttu-id="d5b18-155">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="d5b18-155">**DataRowCollection**</span></span>|<span data-ttu-id="d5b18-156">TableName</span><span class="sxs-lookup"><span data-stu-id="d5b18-156">TableName</span></span>|<span data-ttu-id="d5b18-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="d5b18-157">typedPlural</span></span>|  
|<span data-ttu-id="d5b18-158">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="d5b18-158">**DataRow**</span></span>|<span data-ttu-id="d5b18-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="d5b18-159">TableNameRow</span></span>|<span data-ttu-id="d5b18-160">typedName</span><span class="sxs-lookup"><span data-stu-id="d5b18-160">typedName</span></span>|  
|<span data-ttu-id="d5b18-161">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="d5b18-161">**DataColumn**</span></span>|<span data-ttu-id="d5b18-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="d5b18-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="d5b18-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="d5b18-163">DataRow.ColumnName</span></span>|<span data-ttu-id="d5b18-164">typedName</span><span class="sxs-lookup"><span data-stu-id="d5b18-164">typedName</span></span>|  
|<span data-ttu-id="d5b18-165">**Property**</span><span class="sxs-lookup"><span data-stu-id="d5b18-165">**Property**</span></span>|<span data-ttu-id="d5b18-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="d5b18-166">PropertyName</span></span>|<span data-ttu-id="d5b18-167">typedName</span><span class="sxs-lookup"><span data-stu-id="d5b18-167">typedName</span></span>|  
|<span data-ttu-id="d5b18-168">**子**アクセサー</span><span class="sxs-lookup"><span data-stu-id="d5b18-168">**Child** Accessor</span></span>|<span data-ttu-id="d5b18-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="d5b18-169">GetChildTableNameRows</span></span>|<span data-ttu-id="d5b18-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="d5b18-170">typedChildren</span></span>|  
|<span data-ttu-id="d5b18-171">**親**アクセサー</span><span class="sxs-lookup"><span data-stu-id="d5b18-171">**Parent** Accessor</span></span>|<span data-ttu-id="d5b18-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="d5b18-172">TableNameRow</span></span>|<span data-ttu-id="d5b18-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="d5b18-173">typedParent</span></span>|  
|<span data-ttu-id="d5b18-174">**データセット**イベント</span><span class="sxs-lookup"><span data-stu-id="d5b18-174">**DataSet** Events</span></span>|<span data-ttu-id="d5b18-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="d5b18-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="d5b18-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="d5b18-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="d5b18-177">typedName</span><span class="sxs-lookup"><span data-stu-id="d5b18-177">typedName</span></span>|  
  
 <span data-ttu-id="d5b18-178">使用する入力**データセット**注釈、次を含める必要があります**xmlns** XML スキーマ定義言語 (XSD) スキーマで参照します。</span><span class="sxs-lookup"><span data-stu-id="d5b18-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="d5b18-179">(データベース テーブルから xsd を作成するを参照してください。<xref:System.Data.DataSet.WriteXmlSchema%2A>または[Visual Studio でのデータセットの操作](http://msdn.microsoft.com/library/8bw9ksd6.aspx))。</span><span class="sxs-lookup"><span data-stu-id="d5b18-179">(To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="d5b18-180">公開する注釈付きスキーマのサンプルを次に示します、**顧客**のテーブル、 **Northwind**リレーションを持つデータベース、 **Orders**含まれているテーブル。</span><span class="sxs-lookup"><span data-stu-id="d5b18-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="d5b18-181">次のコード例は、厳密に型指定された**データセット**サンプル スキーマから作成します。</span><span class="sxs-lookup"><span data-stu-id="d5b18-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="d5b18-182">1 つを使用して<xref:System.Data.SqlClient.SqlDataAdapter>を設定する、**顧客**テーブルと別<xref:System.Data.SqlClient.SqlDataAdapter>を設定する、 **Orders**テーブル。</span><span class="sxs-lookup"><span data-stu-id="d5b18-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="d5b18-183">厳密に型指定**データセット**定義、 **Datarelation**です。</span><span class="sxs-lookup"><span data-stu-id="d5b18-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomeromer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomeromer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5b18-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5b18-184">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="d5b18-185">型指定されたデータセット</span><span class="sxs-lookup"><span data-stu-id="d5b18-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="d5b18-186">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="d5b18-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d5b18-187">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="d5b18-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
