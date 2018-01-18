---
title: "SQL XML 列値"
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
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c31ec6ae2b50870da7b999e20cd8ae44f1d42e03
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sql-xml-column-values"></a>SQL XML 列値
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] では、新たに `xml` データ型をサポートしています。開発者は、<xref:System.Data.SqlClient.SqlCommand> クラスの標準動作を使用して、この型を含む結果セットを取得することができます。 `xml` 列は、その他の列と同じようにして (<xref:System.Data.SqlClient.SqlDataReader> などに) 取得することができますが、その列の内容を XML として使用する場合は、<xref:System.Xml.XmlReader> を使用する必要があります。  
  
## <a name="example"></a>例  
 次のコンソール アプリケーションが各を含む 2 つの行を選択、`xml`列から、 **Sales.Store**テーブルに、 **AdventureWorks**データベースを<xref:System.Data.SqlClient.SqlDataReader>インスタンス。 それぞれの行について、`xml` 列の値は、<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して読み取ります。 値は、<xref:System.Xml.XmlReader> に格納されます。 内容を <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 変数に設定する場合は、<xref:System.Data.IDataRecord.GetValue%2A> メソッドではなく <xref:System.Data.SqlTypes.SqlXml> を使用する必要があることに注意してください。<xref:System.Data.IDataRecord.GetValue%2A> は、`xml` 列の値を文字列として返します。  
  
> [!NOTE]
>  **AdventureWorks**をインストールするときに、サンプル データベースが既定でインストールされていない[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Setup を実行してインストールします。  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.SqlTypes.SqlXml>  
 [SQL Server における XML データ](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
