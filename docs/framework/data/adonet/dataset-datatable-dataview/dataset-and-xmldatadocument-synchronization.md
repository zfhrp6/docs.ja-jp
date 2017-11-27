---
title: "DataSet と XmlDataDocument の同期"
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
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 923a6b6cf1523c8a11cb509679443b9658e07ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="8da5c-102">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="8da5c-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="8da5c-103">ADO.NET の <xref:System.Data.DataSet> には、データのリレーショナル表現があります。</span><span class="sxs-lookup"><span data-stu-id="8da5c-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="8da5c-104">階層データにアクセスするには、.NET Framework で使用できる XML クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="8da5c-105">従来、この 2 つのデータ表現は個別に使用されていました。</span><span class="sxs-lookup"><span data-stu-id="8da5c-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="8da5c-106">ただし、.NET Framework によりを使用してデータのリレーショナルおよび階層表現の両方へリアルタイムに同期のアクセス、**データセット**オブジェクトおよび<xref:System.Xml.XmlDataDocument>オブジェクト、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="8da5c-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="8da5c-107">ときに、**データセット**と同期されて、 **XmlDataDocument**、両方のオブジェクトは単一のデータのセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="8da5c-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="8da5c-108">つまり、変更する場合、**データセット**で、変更が反映されます、 **XmlDataDocument**、およびその逆です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="8da5c-109">間のリレーションシップ、**データセット**と**XmlDataDocument**の構築されたサービス スイート全体にアクセスする、データの 1 つのセットを使用して、1 つのアプリケーションを許可することで優れた柔軟性を作成囲む、**データセット**(Web フォームや Windows フォーム コントロールの Visual Studio .NET デザイナーなど)、Extensible Stylesheet Language (XSL)、XSL Transformations (XSLT)、および XML パスを含む XML サービス スイートのだけでなく言語 (XPath)。</span><span class="sxs-lookup"><span data-stu-id="8da5c-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="8da5c-110">アプリケーションでアクセス対象とするサービス セットを選択する必要はありません。どちらのサービス セットにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="8da5c-111">同期するいくつかの方法、**データセット**で、 **XmlDataDocument**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="8da5c-112">次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-112">You can:</span></span>  
  
-   <span data-ttu-id="8da5c-113">追加、**データセット**スキーマ (つまり、リレーショナル構造) とデータを使用し、それを新しい同期**XmlDataDocument**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="8da5c-114">この方法では、既存のリレーショナル データの階層ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="8da5c-115">例:</span><span class="sxs-lookup"><span data-stu-id="8da5c-115">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   <span data-ttu-id="8da5c-116">追加、**データセット**スキーマのみを使用 (厳密に型指定されたなど**データセット**)、同期で、 **XmlDataDocument**、し、ロード、 **XmlDataDocument** XML ドキュメントからです。</span><span class="sxs-lookup"><span data-stu-id="8da5c-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="8da5c-117">この方法では、既存の階層データのリレーショナル ビューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="8da5c-118">テーブル名と列名、**データセット**スキーマは、同期をとる XML 要素の名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8da5c-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="8da5c-119">この名前の一致では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="8da5c-120">なおのスキーマ、**データセット**のみ、リレーショナル ビューで公開する、XML 要素と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8da5c-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="8da5c-121">つまり、このドキュメント上に非常に大きい XML ドキュメントと非常に小さなリレーショナル ウィンドウを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="8da5c-122">**XmlDataDocument**いなくても、XML ドキュメント全体を保持、**データセット**ことの一部を公開するだけです。</span><span class="sxs-lookup"><span data-stu-id="8da5c-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="8da5c-123">(これの詳細な例についてを参照してください[DataSet と XmlDataDocument の同期](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)。)。</span><span class="sxs-lookup"><span data-stu-id="8da5c-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="8da5c-124">次のコード例を作成するための手順を示しています、**データセット**してそのスキーマを読み込みと同期して、 **XmlDataDocument**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="8da5c-125">なお、**データセット**スキーマだけの要素を照合する必要があります、 **XmlDataDocument**を使用して公開する、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="8da5c-126">読み込むことはできません、 **XmlDataDocument**と同期されている場合、**データセット**データが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="8da5c-127">読み込もうとすると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="8da5c-128">新規作成**XmlDataDocument** 、XML ドキュメントからそれを読み込むしを使用して、データのリレーショナル ビューにアクセスし、**データセット**のプロパティ、 **XmlDataDocument**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="8da5c-129">スキーマを設定する必要があります、**データセット**内のデータのいずれかを表示する前に、 **XmlDataDocument**を使用して、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="8da5c-130">ここでも、テーブル名と列名が、**データセット**スキーマは、同期をとる XML 要素の名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8da5c-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="8da5c-131">この名前の一致では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="8da5c-132">次のコード例は、内のデータのリレーショナル ビューにアクセスする方法を示しています、 **XmlDataDocument**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="8da5c-133">同期するもう 1 つの利点、 **XmlDataDocument**で、**データセット**XML ドキュメントの忠実性が維持されることができます。</span><span class="sxs-lookup"><span data-stu-id="8da5c-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="8da5c-134">場合、**データセット**による XML ドキュメントから読み込んだ**ReadXml**として XML ドキュメントを使用して、バックアップ データが書き込まれるときに、 **WriteXml**から大幅に異なる場合があります、元の XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="8da5c-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="8da5c-135">これは、ため、**データセット**空白、または XML ドキュメントからの要素の順序などの階層情報などの書式設定を保持しません。</span><span class="sxs-lookup"><span data-stu-id="8da5c-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="8da5c-136">**データセット**もこれらのスキーマが一致しないために無視された XML ドキュメントから要素を含んでいない、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="8da5c-137">同期中、 **XmlDataDocument**で、**データセット**で保持するのには、元の XML ドキュメントの書式設定や階層要素の構造、 **XmlDataDocument**中、**データセット**データとスキーマの適切な情報だけを含む、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="8da5c-138">同期するときに、**データセット**で、 **XmlDataDocument**、かどうかによって結果が異なる場合があります、<xref:System.Data.DataRelation>オブジェクトが入れ子になった。</span><span class="sxs-lookup"><span data-stu-id="8da5c-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="8da5c-139">詳細については、次を参照してください。 [Datarelation の入れ子](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8da5c-140">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8da5c-140">In This Section</span></span>  
 [<span data-ttu-id="8da5c-141">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="8da5c-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="8da5c-142">厳密に型指定の同期を示しています**データセット**、最小限のスキーマで、 **XmlDataDocument**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="8da5c-143">DataSet に対する XPath クエリの実行</span><span class="sxs-lookup"><span data-stu-id="8da5c-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="8da5c-144">内容に対する XPath クエリの実行を示しています、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="8da5c-145">XSLT 変換をデータセットに適用します。</span><span class="sxs-lookup"><span data-stu-id="8da5c-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="8da5c-146">内容に対する XSLT 変換の適用を示しています、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8da5c-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="8da5c-147">Related Sections</span></span>  
 [<span data-ttu-id="8da5c-148">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="8da5c-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="8da5c-149">について説明しますが、どのように**データセット**読み込みの内容を保持するなど、データ ソースとして XML と対話、**データセット**XML データとして。</span><span class="sxs-lookup"><span data-stu-id="8da5c-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="8da5c-150">Datarelation の入れ子化</span><span class="sxs-lookup"><span data-stu-id="8da5c-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="8da5c-151">重要性について説明入れ子になった**DataRelation**オブジェクトの内容を表す時に、**データセット**XML データとしてこれらのリレーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8da5c-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="8da5c-152">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="8da5c-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="8da5c-153">について説明します、**データセット**およびアプリケーション データを管理し、リレーショナル データベースや XML などのデータ ソースと対話する方法です。</span><span class="sxs-lookup"><span data-stu-id="8da5c-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="8da5c-154">に関するリファレンス情報を含む、 **XmlDataDocument**クラスです。</span><span class="sxs-lookup"><span data-stu-id="8da5c-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da5c-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="8da5c-155">See Also</span></span>  
 [<span data-ttu-id="8da5c-156">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="8da5c-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
