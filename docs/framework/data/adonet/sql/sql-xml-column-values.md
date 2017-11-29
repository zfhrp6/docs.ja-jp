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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c974749ee84bf64d1912ed71ea0817227b1ea514
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="3cfb5-102">SQL XML 列値</span><span class="sxs-lookup"><span data-stu-id="3cfb5-102">SQL XML Column Values</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="3cfb5-103"> では、新たに `xml` データ型をサポートしています。開発者は、<xref:System.Data.SqlClient.SqlCommand> クラスの標準動作を使用して、この型を含む結果セットを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-103"> supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="3cfb5-104">`xml` 列は、その他の列と同じようにして (<xref:System.Data.SqlClient.SqlDataReader> などに) 取得することができますが、その列の内容を XML として使用する場合は、<xref:System.Xml.XmlReader> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cfb5-105">例</span><span class="sxs-lookup"><span data-stu-id="3cfb5-105">Example</span></span>  
 <span data-ttu-id="3cfb5-106">次のコンソール アプリケーションが各を含む 2 つの行を選択、`xml`列から、 **Sales.Store**テーブルに、 **AdventureWorks**データベースを<xref:System.Data.SqlClient.SqlDataReader>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="3cfb5-107">それぞれの行について、`xml` 列の値は、<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して読み取ります。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="3cfb5-108">値は、<xref:System.Xml.XmlReader> に格納されます。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3cfb5-109">内容を <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 変数に設定する場合は、<xref:System.Data.IDataRecord.GetValue%2A> メソッドではなく <xref:System.Data.SqlTypes.SqlXml> を使用する必要があることに注意してください。<xref:System.Data.IDataRecord.GetValue%2A> は、`xml` 列の値を文字列として返します。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cfb5-110">**AdventureWorks**をインストールするときに、サンプル データベースが既定でインストールされていない[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-110">The **AdventureWorks** sample database is not installed by default when you install [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3cfb5-111">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Setup を実行してインストールします。</span><span class="sxs-lookup"><span data-stu-id="3cfb5-111">You can install it by running [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3cfb5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cfb5-112">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="3cfb5-113">SQL Server の XML データ</span><span class="sxs-lookup"><span data-stu-id="3cfb5-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="3cfb5-114">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="3cfb5-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
