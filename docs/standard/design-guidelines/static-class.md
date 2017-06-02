---
title: "静的クラスのデザイン | Microsoft Docs"
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
  - "型のデザインのガイドライン、静的クラス"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] クラス"
  - "静的クラス [.NET Framework]"
  - "静的クラス [.NET Framework]"
  - "クラス [.NET Framework] のデザイン ガイドライン"
  - "クラス型の設計ガイドライン"
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 静的クラスのデザイン
静的クラスが静的メンバーのみが含まれるクラスとして定義されている \(もちろんから継承されたインスタンスのメンバーだけでなく <xref:System.Object?displayProperty=fullName> とコンス トラクターはプライベート可能性があります\)。 一部の言語では、静的クラスの組み込みサポートを提供します。 C\# 2.0 以降では、クラスが静的に宣言されると、シール、抽象クラスで、あるインスタンス メンバーをオーバーライドまたは宣言されていることができます。  
  
 静的クラスは、純粋なオブジェクト指向設計と単純さのバランスです。 その他の操作へのショートカットを提供によく使用されます \(よう <xref:System.IO.File?displayProperty=fullName>\)、拡張メソッド、または完全なオブジェクト指向のラッパーが保証されているいない機能の保持者 \(など <xref:System.Environment?displayProperty=fullName>\)。  
  
 **✓ は** 静的クラスは控えめに使用します。  
  
 静的クラスは、オブジェクト指向のコア フレームワークのサポート クラスとしてのみ使用する必要があります。  
  
 **X のしないで** 雑バケットとして静的クラスを処理します。  
  
 **X のしないで** 宣言または静的クラスのインスタンス メンバーをオーバーライドします。  
  
 **✓ は** シール、抽象クラスで静的クラスを宣言し、使用するプログラミング言語には静的クラスの組み込みサポートがない場合、プライベート インスタンス コンス トラクターを追加します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)