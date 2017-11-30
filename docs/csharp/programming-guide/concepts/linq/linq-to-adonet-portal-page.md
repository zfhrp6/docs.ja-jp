---
title: "LINQ to ADO.NET (ポータル ページ)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 649497f28ef5f9758ba6d6df13a91a1246d12136
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (ポータル ページ)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] では、[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] プログラミング モデルを使用して [!INCLUDE[vstecado](~/includes/vstecado-md.md)] 内の列挙可能なオブジェクトに対してクエリを実行できます。  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] のドキュメントについては、.NET Framework SDK の「[LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)」の ADO.NET のセクションを参照してください。  
  
 ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] には、[!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、および [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] の 3 つのテクノロジがあります。 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] は、<xref:System.Data.DataSet> に対する高度で最適化されたクエリの実行を可能にします。一方、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] は、[!INCLUDE[ssNoVersion](~/includes/ssnoversion-md.md)] データベース スキーマに対して直接クエリを実行できるようにします。また、[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] は、[!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)] をクエリできるようにします。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> は、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] で最も幅広く使用されているコンポーネントの 1 つであり、[!INCLUDE[vstecado](~/includes/vstecado-md.md)] の基礎である非接続型プログラミングの重要な要素です。 こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限もあります。  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] では、他の多くのデータ ソースで使用できるのと同じクエリ機能を使用することで、豊富なクエリ機能を <xref:System.Data.DataSet> に組み込むことができます。  
  
 詳細については、「[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)」を参照してください。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] には、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャが用意されています。 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。 アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。 データベースから結果が返されると、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] で元の操作できるオブジェクトに変換されます。  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] には、データベースのストアド プロシージャ、ユーザー定義関数、オブジェクト モデルの継承のサポートが含まれています。  
  
 詳細については、「[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)」を参照してください。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)]を介して、リレーショナル データは .NET 環境でオブジェクトとして公開されます。 これにより、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。 この機能は、[!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] と呼ばれます。 LINQ の詳細については、「[LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
 [統合言語クエリ (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
