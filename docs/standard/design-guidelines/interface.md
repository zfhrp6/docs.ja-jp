---
title: "インターフェイスのデザイン | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "インターフェイス [.NET Framework] のデザイン ガイドライン"
  - "型のデザインのガイドライン、インターフェイス"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] インターフェイス"
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# インターフェイスのデザイン
ほとんどの Api は、クラスと構造体を使用して、最適なモデル化、またはインターフェイスがより適切な唯一のオプションの場合もあります。  
  
 CLR は多重継承をサポートしていません \(つまり、CLR クラスできない複数の基本クラスから継承\) が、基本クラスから継承するだけでなく、1 つまたは複数のインターフェイスを実装する型。 したがって、インターフェイスは、多重継承の効果を実現するためによく使用されます。 たとえば、 <xref:System.IDisposable> インターフェイスにより、参加する継承階層の独立した disposability をサポートする型です。  
  
 どの定義で、インターフェイスは、適切なその他の状況では、いくつかの値の型を含むいくつかの種類によってサポートされる共通のインターフェイスを作成するのにです。 値型が以外の型から継承できない <xref:System.ValueType>, 、インターフェイスを実装することができますは、共通の基本型を提供するためには、唯一のオプションは、インターフェイスを使用しています。  
  
 **✓ は** 一部共通の API を値型を含む一連の型でサポートする必要がある場合は、インターフェイスを定義します。  
  
 **✓ を検討してください** 既に別の型から継承した型でその機能をサポートする必要がある場合は、インターフェイスを定義します。  
  
 **X 回避** マーカー インターフェイス \(メンバーを持たないインターフェイス\) を使用します。  
  
 特定の特性 \(マーカー\) されているクラスをマークする必要がある場合は、一般に、インターフェイスではなく、カスタム属性を使用します。  
  
 **✓ は** インターフェイスの実装は、少なくとも 1 つの型を提供します。  
  
 これにより、インターフェイスの設計を検証します。 たとえば、 <xref:System.Collections.Generic.List%601> の実装には、 <xref:System.Collections.Generic.IList%601> インターフェイスです。  
  
 **✓ は** を定義する各インターフェイスを使用するには、少なくとも 1 つの API を提供 \(パラメーターやプロパティとして、インターフェイスを取得するメソッドは、インターフェイスとして型指定された\)。  
  
 これにより、インターフェイスのデザインを検証します。 たとえば、 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=fullName> 消費、 <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> インターフェイスです。  
  
 **X のしないで** 以前に出荷されたインターフェイスにメンバーを追加します。  
  
 この操作と、インターフェイスの実装が損なわします。 バージョン管理の問題を回避するために、新しいインターフェイスを作成する必要があります。  
  
 これらのガイドライン」に記載されている状況以外でマネージ コードの再利用可能なライブラリをデザイン インターフェイスではなく、クラスを選択してください、一般に。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)