---
title: "How to: Generate the Object Model as an External File | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# How to: Generate the Object Model as an External File
属性ベースのマッピングに代わる方法として、SQLMetal コマンド ライン ツールを使用することにより、外部 XML ファイルとしてオブジェクト モデルを生成できます。  詳細については、「[SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」を参照してください。  外部 XML マッピング ファイルを使用すると、コードの煩雑さが軽減されます。  さらに、アプリケーションのバイナリを再コンパイルしなくても、外部ファイルを変更するだけで動作を変えることができます。  詳細については、「[External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]は、外部マッピング ファイルの生成をサポートしていません。  
  
## 使用例  
 次のコマンドは、Northwind サンプル データベースから外部マッピング ファイルを生成します。  
  
```  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## 使用例  
 以下は、Northwind サンプル データベース内の Customers テーブルのマッピングを示す、外部マッピング ファイルの一部分です。  この部分は、**\/map** オプションを使って SQLMetal を実行することによって生成されました。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Database xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="northwnd">  
  <Table Name="Customers">  
    <Type Name=".Customer">  
      <Column Name="CustomerID" Member="CustomerID" Storage="_CustomerID" DbType="NChar(5) NOT NULL" CanBeNull="False" IsPrimaryKey="True" />  
      <Column Name="CompanyName" Member="CompanyName" Storage="_CompanyName" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Member="ContactName" Storage="_ContactName" DbType="NVarChar(30)" />  
      <Column Name="ContactTitle" Member="ContactTitle" Storage="_ContactTitle" DbType="NVarChar(30)" />  
      <Column Name="Address" Member="Address" Storage="_Address" DbType="NVarChar(60)" />  
      <Column Name="City" Member="City" Storage="_City" DbType="NVarChar(15)" />  
      <Column Name="Region" Member="Region" Storage="_Region" DbType="NVarChar(15)" />  
      <Column Name="PostalCode" Member="PostalCode" Storage="_PostalCode" DbType="NVarChar(10)" />  
      <Column Name="Country" Member="Country" Storage="_Country" DbType="NVarChar(15)" />  
      <Column Name="Phone" Member="Phone" Storage="_Phone" DbType="NVarChar(24)" />  
      <Column Name="Fax" Member="Fax" Storage="_Fax" DbType="NVarChar(24)" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" Storage="_CustomerCustomerDemos" ThisKey="CustomerID" OtherTable="CustomerCustomerDemo" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" Storage="_Orders" ThisKey="CustomerID" OtherTable="Orders" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## 参照  
 [Creating the Object Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)   
 [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)   
 [How to: Generate the Object Model in Visual Basic or C\#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)