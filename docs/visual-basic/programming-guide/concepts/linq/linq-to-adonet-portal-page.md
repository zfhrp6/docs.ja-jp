---
title: LINQ to ADO.NET (ポータル ページ)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a266b23856c05c7b5ea07c9020d29b2797c0036
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (ポータル ページ)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] では、[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] プログラミング モデルを使用して [!INCLUDE[vstecado](~/includes/vstecado-md.md)] 内の列挙可能なオブジェクトに対してクエリを実行できます。  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] のドキュメントについては、.NET Framework SDK の「[LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)」の ADO.NET のセクションを参照してください。  
  
 ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] には、[!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、および [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] の 3 つのテクノロジがあります。 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] に対する豊富な最適化されたクエリを提供、 <xref:System.Data.DataSet>、 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server データベース スキーマを直接クエリすることができ、[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]クエリを実行することができます、[!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)]です。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> は、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] で最も幅広く使用されているコンポーネントの 1 つであり、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] の基礎である非接続型プログラミングの重要な要素です。 こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限もあります。  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] では、他の多くのデータ ソースで使用できるのと同じクエリ機能を使用することで、豊富なクエリ機能を <xref:System.Data.DataSet> に組み込むことができます。  
  
 詳細については、「[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] には、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャが用意されています。 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。 アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。 データベースから結果が返されると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] で元の操作できるオブジェクトに変換されます。  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] には、データベースのストアド プロシージャ、ユーザー定義関数、オブジェクト モデルの継承のサポートが含まれています。  
  
 詳細については、「[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)]を介して、リレーショナル データは .NET 環境でオブジェクトとして公開されます。 これにより、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。 この機能は、[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] と呼ばれます。 LINQ の詳細については、「[LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
