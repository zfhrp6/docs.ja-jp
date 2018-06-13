---
title: SQL XML 列値
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 8aa33d2c4558c003d1424e118bdf512d4cafaea9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362738"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="8f4b0-102">SQL XML 列値</span><span class="sxs-lookup"><span data-stu-id="8f4b0-102">SQL XML Column Values</span></span>
<span data-ttu-id="8f4b0-103">SQL Server では、`xml`データ型、および開発者の標準動作を使用してこの型を含む結果セットを取得できます、<xref:System.Data.SqlClient.SqlCommand>クラスです。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="8f4b0-104">`xml` 列は、その他の列と同じようにして (<xref:System.Data.SqlClient.SqlDataReader> などに) 取得することができますが、その列の内容を XML として使用する場合は、<xref:System.Xml.XmlReader> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f4b0-105">例</span><span class="sxs-lookup"><span data-stu-id="8f4b0-105">Example</span></span>  
 <span data-ttu-id="8f4b0-106">次のコンソール アプリケーションが各を含む 2 つの行を選択、`xml`列から、 **Sales.Store**テーブルに、 **AdventureWorks**データベースを<xref:System.Data.SqlClient.SqlDataReader>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="8f4b0-107">それぞれの行について、`xml` 列の値は、<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> の <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して読み取ります。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="8f4b0-108">値は、<xref:System.Xml.XmlReader> に格納されます。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="8f4b0-109">内容を <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> 変数に設定する場合は、<xref:System.Data.IDataRecord.GetValue%2A> メソッドではなく <xref:System.Data.SqlTypes.SqlXml> を使用する必要があることに注意してください。<xref:System.Data.IDataRecord.GetValue%2A> は、`xml` 列の値を文字列として返します。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f4b0-110">**AdventureWorks**既定では、SQL Server をインストールするときにサンプル データベースはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="8f4b0-111">SQL Server Setup を実行してインストールします。</span><span class="sxs-lookup"><span data-stu-id="8f4b0-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8f4b0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f4b0-112">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="8f4b0-113">SQL Server における XML データ</span><span class="sxs-lookup"><span data-stu-id="8f4b0-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="8f4b0-114">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="8f4b0-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
