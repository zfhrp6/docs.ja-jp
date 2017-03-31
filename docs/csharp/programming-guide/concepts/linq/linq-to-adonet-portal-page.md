---
title: "LINQ to ADO.NET (ポータル ページ) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f1c70901d5c2e5f5d709ec3c10821fbd1aa9dee6
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (ポータル ページ)
[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] では、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] プログラミング モデルを使用して [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] 内の列挙可能なオブジェクトに対してクエリを実行できます。  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] のドキュメントについては、.NET Framework SDK の「[LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)」の ADO.NET のセクションを参照してください。  
  
 ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] には、[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、および [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] の 3 つのテクノロジがあります。 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] は、<xref:System.Data.DataSet> に対する高度で最適化されたクエリの実行を可能にします。一方、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] は、[!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)] データベース スキーマに対して直接クエリを実行できるようにします。また、[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] は、[!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)] をクエリできるようにします。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> は、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] で最も幅広く使用されているコンポーネントの 1 つであり、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] の基礎である非接続型プログラミングの重要な要素です。 こうした突出した特長がある反面、<xref:System.Data.DataSet> のクエリ機能には制限もあります。  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] では、他の多くのデータ ソースで使用できるのと同じクエリ機能を使用することで、豊富なクエリ機能を <xref:System.Data.DataSet> に組み込むことができます。  
  
 詳細については、「[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)」を参照してください。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] には、リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャが用意されています。 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] では、リレーショナル データベースのデータ モデルが、開発者のプログラミング言語で表されるオブジェクト モデルに対応付けられています。 アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] は、オブジェクト モデルの統合言語クエリを SQL に変換し、それをデータベースに送信して実行します。 データベースから結果が返されると、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] で元の操作できるオブジェクトに変換されます。  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] には、データベースのストアド プロシージャ、ユーザー定義関数、オブジェクト モデルの継承のサポートが含まれています。  
  
 詳細については、「[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)」を参照してください。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]を介して、リレーショナル データは .NET 環境でオブジェクトとして公開されます。 これにより、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。 この機能は、[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] と呼ばれます。 LINQ の詳細については、「[LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)   
 [統合言語クエリ (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
