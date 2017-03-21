---
title: "LINQ to ADO.NET (ポータル ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5c71b304dbff960320b1a9f46e38259705b8dadc
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (ポータル ページ)
[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]内の列挙可能なオブジェクトに対するクエリを実行することができます[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]を使用して、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]プログラミング モデルです。  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]ドキュメントは、.NET Framework SDK の ADO.NET セクションにあります: [LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)します。  
  
 ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] には、[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、および [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] の&3; つのテクノロジがあります。 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]豊富な最適化されたクエリを実行するには、 <xref:System.Data.DataSet>、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]を直接照会することができます[!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)]データベース スキーマ、および[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]クエリを実行することができます、 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]</xref:System.Data.DataSet> 。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet>で最も広く使用されているコンポーネントの&1; つ[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]とは、非接続型プログラミングの重要な要素をモデル化[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]は上に構築します</xref:System.Data.DataSet>。 ただし、この重要であるにもかかわらず、<xref:System.Data.DataSet>クエリ機能が制限されています</xref:System.Data.DataSet>。  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]豊富なクエリ機能を構築することができます<xref:System.Data.DataSet>他の多くのデータ ソースに使用される同じクエリ機能を使用しています</xref:System.Data.DataSet>。  
  
 詳細については、次を参照してください。 [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)します。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]リレーショナル データをオブジェクトとして管理するためのランタイム インフラストラクチャを提供します。 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、リレーショナル データベースのデータ モデルは、開発者のプログラミング言語で表されるオブジェクト モデルにマッピングします。 アプリケーションを実行すると、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]オブジェクト モデルでの統合言語クエリを SQL に変換し、実行するためのデータベースに送信します。 データベースには、結果が返されるときに[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]操作できるオブジェクトにはそれを変換します。  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]オブジェクト モデルでは、ストアド プロシージャと、データベース内のユーザー定義関数、および継承のサポートが含まれています。  
  
 詳細については、次を参照してください。 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)します。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]を介して、リレーショナル データは .NET 環境でオブジェクトとして公開されます。 これにより、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] の利用に最適なオブジェクト レイヤーが実現されます。開発者は、ビジネス ロジックの構築に使用する言語で、データベースを照会するクエリを作成できます。 この機能は、[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] と呼ばれます。 参照してください[LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)の詳細。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)   
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
