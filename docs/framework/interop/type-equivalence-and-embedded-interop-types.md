---
title: "型の等価性と埋め込まれた相互運用機能型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28203dc428db6a2dd06e9c1e85b64ef80e81ffbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="type-equivalence-and-embedded-interop-types"></a>型の等価性と埋め込まれた相互運用機能型
[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降、共通言語ランタイムでは、マネージ アセンブリに COM 型の型情報を直接埋め込めるようになりました。マネージ アセンブリで相互運用アセンブリから COM 型の型情報を取得する必要がありません。 埋め込まれる型情報にはマネージ アセンブリに実際に使用される型とメンバーのみが含まれるため、2 つのマネージ アセンブリで同じ COM 型の表示が非常に異なることが考えられます。 マネージ アセンブリごとに、COM 型の表示を表す異なる <xref:System.Type> オブジェクトが与えられます。 共通言語ランタイムでは、インターフェイス、構造、列挙、委任といった異なる表示間で型の等価性が与えられます。  
  
 型の等価性とは、マネージ アセンブリ間で渡される COM オブジェクトを受け取り側のアセンブリで適切なマネージ型に変換できることを意味します。  
  
> [!NOTE]
>  型の等価性と埋め込まれた相互運用機能型により、COM コンポーネントを利用するアプリケーションとアドインの展開が簡単になります。アプリケーションで相互運用アセンブリを展開する必要がないためです。 ただし、以前のバージョンの .NET Framework でコンポーネントを利用する場合、共有 COM コンポーネントの開発者はプライマリ相互運用アセンブリ (PIA) を作成する必要があります。  
  
## <a name="type-equivalence"></a>型の等価性  
 COM 型の等価性は、インターフェイス、構造、列挙、委任でサポートされています。 COM 型は、次のすべてに該当する場合に等価となります。  
  
-   型がいずれもインターフェイスであるか、いずれも構造であるか、いずれも列挙であるか、いずれも委任である。  
  
-   型の ID が同じである (次のセクションに詳細あり)。  
  
-   いずれの型も、型の等価性に適合する (「[型の等価性の資格ありとして COM 型を設定する](#type_equiv)」セクションに詳細あり)。  
  
### <a name="type-identity"></a>型の ID  
 範囲と ID が一致するとき、言い換えると、それぞれに <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性が含まれ、2 つの属性の <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> プロパティと <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> プロパティが一致する場合、2 つの型の ID が同じであると判断されます。 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> の比較では、大文字と小文字が区別されません。  
  
 型に <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性が含まれない場合、あるいは範囲や識別子を指定しない <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性が型に含まれる場合も、型は次のように等価性適用として考慮されます。  
  
-   インターフェイスの場合、<xref:System.Runtime.InteropServices.GuidAttribute> の値が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> プロパティの代わりに使用されます。<xref:System.Type.FullName%2A?displayProperty=nameWithType> プロパティ (つまり、名前空間を含む、型の名前) が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> プロパティの代わりに使用されます。  
  
-   構造、列挙、委任の場合、含んでいるアセンブリの <xref:System.Runtime.InteropServices.GuidAttribute> が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> プロパティの代わりに使用されます。<xref:System.Type.FullName%2A?displayProperty=nameWithType> プロパティが <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> プロパティの代わりに使用されます。  
  
<a name="type_equiv"></a>   
### <a name="marking-com-types-for-type-equivalence"></a>型の等価性に適合するものとして COM 型を設定する  
 型の等価性に適合するものとして 2 つの方法で型を設定できます。  
  
-   型に <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性を適用します。  
  
-   型を COM インポート型にします。 <xref:System.Runtime.InteropServices.ComImportAttribute> 属性が与えられていると、インターフェイスは COM インポート型となります。 それが定義されているアセンブリに <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> 属性が含まれる場合、インターフェイス、構造、列挙、委任は COM インポート型となります。  
  
## <a name="see-also"></a>参照  
 <xref:System.Type.IsEquivalentTo%2A>  
 [マネージ コードの COM 型の使用](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
