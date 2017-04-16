---
title: "相互運用のための .NET 型の要件 | Microsoft Docs"
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
  - "COM 相互運用機能, 公開 (COM コンポーネントを)"
  - "COM 相互運用機能, 要件 (.NET 型の)"
  - "公開 (COM に .NET Framework コンポーネントを)"
  - "相互運用 (アンマネージ コードとの), 公開 (.NET Framework コンポーネントを)"
  - "相互運用 (アンマネージ コードとの), 要件 (.NET 型の)"
  - "要件 (相互運用のための .NET 型の)"
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 相互運用のための .NET 型の要件
アセンブリ内の型を COM アプリケーションに公開する場合は、デザイン時に COM 相互運用機能の要件について検討する必要があります。  マネージ型 \(クラス、インターフェイス、構造体、列挙型\) は、次のガイドラインに従うことで、COM 型とシームレスに統合されます。  
  
-   クラスでは、インターフェイスを明示的に実装する必要があります。  
  
     COM 相互運用機能では、クラスのすべてのメンバーと、その基本クラスのメンバーを含んだインターフェイスを自動的に生成する機能が提供されますが、インターフェイスを明示的に実装する方がはるかに優れています。  自動的に生成されるインターフェイスをクラス インターフェイスと呼びます。  ガイドラインについては、「[クラス インターフェイスの概要](http://msdn.microsoft.com/ja-jp/733c0dd2-12e5-46e6-8de1-39d5b25df024)」を参照してください。  
  
     [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C\#、C\+\+ を使うと、インターフェイス定義言語 \(IDL: Interface Definition Language\) またはそれに相当する他の言語を使わなくても、インターフェイス定義をコードに組み込むことができます。  構文の詳細については、使用する言語のドキュメントを参照してください。  
  
-   マネージ型はパブリックである必要があります。  
  
     アセンブリ内で、登録されたり、タイプ ライブラリにエクスポートされたりするのはパブリック型だけです。  そのため、COM から参照できるのはパブリック型だけです。  
  
     マネージ型は他のマネージ コードに対して、COM には公開されない機能を公開します。  たとえば、パラメーター化されたコンストラクター、静的メソッド、定数フィールドは、COM クライアントには公開されません。  また、ランタイムは型のデータを入出力双方にマーシャリングするため、データはコピーまたは変換されることがあります。  
  
-   メソッド、プロパティ、フィールド、およびイベントはパブリックである必要があります。  
  
     パブリック型のメンバーも、COM から参照できるようにする場合には、パブリックである必要があります。  アセンブリ、パブリック型、またはパブリック型のパブリック メンバーの参照可能範囲を制限するには、<xref:System.Runtime.InteropServices.ComVisibleAttribute> を適用します。  既定では、すべてのパブリック型およびメンバーが参照可能です。  
  
-   型は、COM からアクティブ化されるパブリックな既定のコンストラクターを持つ必要があります。  
  
     パブリックなマネージ型は COM から参照できます。  ただし、パブリックな既定のコンストラクター \(引数を持たないコンストラクター\) がない場合、COM クライアントでは型を作成できません。  その他のなんらかの方法でアクティブ化された COM クライアントなら、型を使用できます。  
  
-   型を抽象型にすることはできません。  
  
     COM クライアントでも、.NET クライアントでも、抽象型は生成できません。  
  
 マネージ型の継承の階層構造は、COM にエクスポートされると平坦になり、階層がなくなります。  マネージ環境とアンマネージ環境では、バージョン管理も異なります。  COM に公開される型は、他のマネージ型と同じバージョン管理特性を持ちません。  
  
## 参照  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [Introducing the Class Interface](http://msdn.microsoft.com/ja-jp/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [相互運用固有の属性の適用](../../../docs/framework/interop/applying-interop-attributes.md)   
 [COM 用のアセンブリのパッケージ化](../../../docs/framework/interop/packaging-an-assembly-for-com.md)