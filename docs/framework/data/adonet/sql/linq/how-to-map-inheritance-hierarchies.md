---
title: "方法 : 継承階層を割り当てる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e9d6215335f6a58de194253cbfe1e539f50d6d84
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-map-inheritance-hierarchies"></a>方法 : 継承階層を割り当てる
[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] で継承の割り当てを実装するには、以下の手順で示すように、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している開発者は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して継承階層を割り当てることができます。 参照してください[する方法: O/R デザイナーを使用して継承を構成する](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)です。  
  
> [!NOTE]
>  サブクラスには特別な属性やプロパティは必要ありません。 特に、サブクラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性がない点に注意してください。  
  
### <a name="to-map-an-inheritance-hierarchy"></a>継承階層を割り当てるには  
  
1.  ルート クラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加します。  
  
2.  ルート クラスに対し、階層構造の各クラスについて <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性を追加します。  
  
3.  各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> プロパティを定義します。  
  
     このプロパティは、データベース テーブルの <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 列に含まれる値を保持し、このデータ行が属するクラスまたはサブクラスを示します。  
  
4.  各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> プロパティも追加します。  
  
     このプロパティは、キー値が示すクラスまたはサブクラスを表す値を保持します。  
  
5.  1 つの <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性にのみ、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> プロパティを追加します。  
  
     このプロパティに指定するのには、*フォールバック*データベース テーブルから識別子の値に一致しない場合、マッピング<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>継承の割り当て値。  
  
6.  <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
     このプロパティは、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 値を保持する列であることを示します。  
  
## <a name="example"></a>例  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用して継承を構成できます。 参照してください[する方法: O/R デザイナーを使用して継承を構成します。](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 次のコード例では、`Vehicle` をルート クラスとして定義し、ここまでの手順を実装して、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] の階層構造を指定します。  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>参照  
 [継承のサポート](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)  
 [方法 : コード エディターを使用してエンティティ クラスをカスタマイズする](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
