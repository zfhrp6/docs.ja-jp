---
title: "配列 | Microsoft Docs"
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
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] 配列"
  - "配列 [.NET Framework] の使用に関するガイドライン"
  - "空の配列"
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 配列
**✓ は** パブリック Api の配列にコレクションの使用を希望します。[コレクション](../../../docs/standard/design-guidelines/guidelines-for-collections.md) セクションでは、コレクションと配列の間での選択方法の詳細を説明します。  
  
 **X のしないで** 読み取り専用配列フィールドを使用します。 フィールド自体は読み取り専用と、変更できない配列内の要素を変更することができます。  
  
 **✓ を検討してください** 多次元配列ではなくジャグ配列を使用します。  
  
 ジャグ配列は、要素も配列を含む配列です。 小さいは無駄な空間データ \(たとえば、スパース マトリックス\) セットによって多次元配列と比較する、さまざまなサイズの要素を構成する配列ができます。 さらに、CLR は、一部のシナリオで、実行時のより優れたパフォーマンスを発生する可能性がありますので、ジャグ配列のインデックス操作を最適化します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 <xref:System.Array>   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)