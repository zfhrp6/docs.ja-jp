---
title: "型の等価性と埋め込まれた相互運用機能型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "埋め込まれた相互運用機能型"
  - "NoPIA"
  - "プライマリ相互運用機能アセンブリ, 不要 (CLR バージョン 4)"
  - "型の等価性"
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# 型の等価性と埋め込まれた相互運用機能型
[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降の共通言語ランタイムでは、COM 型の型情報をマネージ アセンブリに直接埋め込むことができ、マネージ アセンブリで COM 型の型情報を相互運用機能アセンブリから取得する必要はありません。  埋め込み型情報に含まれるのはマネージ アセンブリで実際に使用される型とメンバーだけなので、同じ COM 型のビューでも 2 つのマネージ アセンブリで大きく異なる場合があります。  各マネージ アセンブリには、COM 型のビューを表す異なる <xref:System.Type> オブジェクトがあります。  共通言語ランタイムでは、インターフェイス、構造体、列挙体、およびデリゲートについて、これらの異なるビュー間における型の等価性をサポートしています。  
  
 型の等価性とは、あるマネージ アセンブリから別のマネージ アセンブリに渡される COM オブジェクトを、受け取り側のアセンブリの適切なマネージ型にキャストできることです。  
  
> [!NOTE]
>  型の等価性と埋め込まれた相互運用機能型を利用すると、アプリケーションで相互運用機能アセンブリを配置する必要がなくなるため、COM コンポーネントを使用するアプリケーションおよびアドインの配置が簡単になります。  共有 COM コンポーネントの開発者は、それらのコンポーネントを以前のバージョンの .NET Framework で使用するには、これまで同様、プライマリ相互運用機能アセンブリ \(PIA: Primary Interop Assemblies\) を作成する必要があります。  
  
## 型の等価性  
 COM 型の等価性は、インターフェイス、構造体、列挙体、およびデリゲートに対してサポートされます。  COM 型が等価と見なされるのは、次の条件がすべて満たされた場合です。  
  
-   型が、どちらもインターフェイス、構造体、列挙体、またはデリゲートである。  
  
-   型の ID が同じである。詳細については、次の節を参照してください。  
  
-   どちらの型も型の等価性を利用できる。詳細については、「[型の等価性を利用できるように COM 型を指定する](#type_equiv)」を参照してください。  
  
### 型の ID  
 2 つの型の ID が同じと見なされるのは、それらの型のスコープと ID が一致する場合です。つまり、それぞれの型に <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性があり、この 2 つの属性の <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> プロパティと <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> プロパティが一致する場合です。  <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> の比較では、大文字と小文字が区別されません。  
  
 型に <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性がない場合でも、または <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性はあるがスコープと ID が指定されていない場合でも、次のように、等価かどうか評価されます。  
  
-   インターフェイスの場合、<xref:System.Runtime.InteropServices.GuidAttribute> の値が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=fullName> プロパティの代わりに使用され、<xref:System.Type.FullName%2A?displayProperty=fullName> プロパティ \(つまり、名前空間を含む型名\) が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=fullName> プロパティの代わりに使用されます。  
  
-   構造体、列挙体、およびデリゲートの場合、それらを含んでいるアセンブリの <xref:System.Runtime.InteropServices.GuidAttribute> が <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> プロパティの代わりに使用され、<xref:System.Type.FullName%2A?displayProperty=fullName> プロパティが <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> プロパティの代わりに使用されます。  
  
<a name="type_equiv"></a>   
### 型の等価性を利用できるように COM 型を指定する  
 型の等価性を利用できるように型を指定するには、次の 2 つの方法があります。  
  
-   <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性を型に適用します。  
  
-   型を COM インポート型にします。  インターフェイスは、<xref:System.Runtime.InteropServices.ComImportAttribute> 属性が設定されている場合、COM インポート型になります。  インターフェイス、構造体、列挙体、またはデリゲートは、その定義元のアセンブリに <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> 属性が設定されている場合、COM インポート型になります。  
  
## 参照  
 <xref:System.Type.IsEquivalentTo%2A>   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/ja-jp/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)