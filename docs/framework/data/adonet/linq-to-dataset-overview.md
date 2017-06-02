---
title: "LINQ to DataSet Overview | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# LINQ to DataSet Overview
<xref:System.Data.DataSet> は、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] のコンポーネントの中でもきわめて使用頻度の高いコンポーネントの 1 つです。 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の基礎を成す非接続型プログラミング モデルの重要な要素であり、さまざまなデータ ソースからのデータを明示的にキャッシュできます。 プレゼンテーション層では、<xref:System.Data.DataSet> とデータ バインドの GUI コントロールとが密接に連携します。 中間層では、リレーショナル形式のデータを維持するキャッシュとして機能し、単純で高速なクエリと、階層的なナビゲーション サービスを提供します。  データベースに対する要求数を削減するための基本的な手法は、<xref:System.Data.DataSet> を使用し、データを中間層でキャッシュすることです。  たとえば、データ ドリブンの [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションでは、  ほとんど変更されないアプリケーション データがかなりの割合で存在し、しかも、複数のセッションまたは複数のユーザー間で共通して使用されているケースがよくあります。  このデータを Web サーバー上のメモリに維持しておくことで、データベースに対する要求数を減らし、高速な対話処理をユーザーに提供できます。  <xref:System.Data.DataSet> が備えるもう 1 つの特長は、アプリケーションが、1 つまたは複数のデータ ソースから取得したデータのサブセットをアプリケーション空間に取り込むことができる点です。  アプリケーションは、そのデータをリレーショナル形式を維持したままインメモリで操作できます。  
  
 こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限があります。  <xref:System.Data.DataTable.Select%2A> メソッドでデータのフィルター処理や並べ替えを行ったり、<xref:System.Data.DataRow.GetChildRows%2A> メソッドや <xref:System.Data.DataRow.GetParentRow%2A> メソッドを使って階層のナビゲーションを行うことはできます。  しかし、さらに複雑な処理を行うには、開発者が独自にクエリを作成する必要があります。  その結果、アプリケーションで期待したパフォーマンスが得られなかったり、メンテナンスが難しくなったりする可能性があります。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、<xref:System.Data.DataSet> オブジェクトにキャッシュされたデータに対するクエリをより簡単に、より高速にします。  これらのクエリはアプリケーション コードに文字列リテラルとして記述するのではなく、プログラミング言語そのもので表現できます。  つまり、開発者はクエリ言語を個別に習得する必要はありません。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] の利点はそれだけではありません。[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE で [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] に対するコンパイル時の構文チェック、静的な型指定、IntelliSense などの機能を利用できるため、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 開発者の生産性も向上します。  また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用すると、1 つまたは複数のデータ ソースから取得して統合したデータを照会することもできます。  これにより、データの表現方法や扱いに柔軟性が要求されるさまざまなシナリオが実現します。  特に、汎用のレポート作成、分析、ビジネス インテリジェンスを行うアプリケーションでは、この手法を用いたデータ操作が欠かせません。  
  
## LINQ to DataSet を使った DataSet のクエリ  
 <xref:System.Data.DataSet> を使用して [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] オブジェクトを照会するには、あらかじめ <xref:System.Data.DataSet> にデータを読み込んでおく必要があります。 <xref:System.Data.DataSet> へのデータの読み込みは、<xref:System.Data.Common.DataAdapter> クラスまたは [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md) を使用するなど、複数の方法で行うことができます。  <xref:System.Data.DataSet> オブジェクトへのデータの読み込みが完了すると、そのデータセットに対してクエリを実行できるようになります。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使ったクエリの作成方法は、他の [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 対応データ ソースに対して [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] を使用する方法と似ています。  [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] のクエリは、<xref:System.Data.DataSet> の単一のテーブルに対して実行するか、または <xref:System.Linq.Enumerable.Join%2A> や <xref:System.Linq.Enumerable.GroupJoin%2A> などの標準クエリ演算子を使って複数のテーブルに対して実行することができます。  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] のクエリは、<xref:System.Data.DataSet> の型指定されたオブジェクトと、型指定されていないオブジェクトの両方をサポートしています。  アプリケーションのデザイン時に <xref:System.Data.DataSet> のスキーマがわかっている場合は、型指定された <xref:System.Data.DataSet> を使用することをお勧めします。 型指定された <xref:System.Data.DataSet> のテーブルおよび行は、列ごとに型指定されたメンバーを持ちます。これにより、クエリが簡素化され、読みやすくなります。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] には、System.Core.dll に実装された標準クエリ演算子に加え、一連の <xref:System.Data.DataSet> オブジェクトに対して容易にクエリを実行することのできる複数の <xref:System.Data.DataRow> 固有の拡張機能が追加されています。  これらの <xref:System.Data.DataSet> 固有の拡張機能には、<xref:System.Data.DataRow> の列値にアクセスするためのメソッドのほか、一連の行を比較するための演算子があります。  
  
## n 層アプリケーションと LINQ to DataSet  
 n 層データ アプリケーションは、複数の論理レイヤー \(層\) に分けられた、データ処理を中心とするアプリケーションです。  一般に、n 層アプリケーションには、プレゼンテーション層、中間層、およびデータ層が含まれます。  アプリケーション コンポーネントを別個の層に分離すると、アプリケーションの保守容易性とスケーラビリティが向上します。  n 層データ アプリケーションの詳細については、「[n 層アプリケーションでのデータセットの操作](../Topic/Work%20with%20datasets%20in%20n-tier%20applications.md)」を参照してください。  
  
 n 層アプリケーションでは、Web アプリケーションの情報をキャッシュするために <xref:System.Data.DataSet> が中間層で使用されます。  拡張メソッドを通じて実装される [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のクエリ機能により、既存の ADO.NET 2.0 の <xref:System.Data.DataSet> が強化されています。  
  
## 参照  
 [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)