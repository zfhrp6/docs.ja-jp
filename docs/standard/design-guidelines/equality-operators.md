---
title: "等値演算子 | Microsoft Docs"
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
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] Equals メソッド"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] 等値演算子"
  - "等値演算子 (= =) [.NET Framework]"
  - "Equals メソッド"
  - "= 演算子 (等値) [.NET Framework]"
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 等値演算子
ここではオーバー ロードの等値演算子について説明し、指す `operator==` と `operator!=` 等値演算子とします。  
  
 **X のしないで** 等値演算子のいずれかのオーバー ロードします。  
  
 **✓ は** いることを確認 <xref:System.Object.Equals%2A?displayProperty=fullName> 等値演算子は、同じセマンティクスと類似のパフォーマンス特性があるとします。  
  
 多くの場合、つまり、この `Object.Equals` 等値演算子はオーバー ロード時に上書きする必要があります。  
  
 **X 回避** 等値演算子から例外をスローします。  
  
 たとえば、引数のいずれかがスローする代わりに null の場合は false を返す `NullReferenceException`します。  
  
## 値の型で等値演算子  
 **✓ は** 等しいかどうかが意味のある場合は、値型で等値演算子をオーバー ロードします。  
  
 ほとんどのプログラミング言語での既定の実装はありません `operator==` 値型です。  
  
## 参照型で等値演算子  
 **X 回避** 変更可能な参照型で等値演算子のオーバー ロードします。  
  
 多くの言語では、参照型に関する組み込みの等値演算子があります。 組み込み演算子は通常、参照の等価性を実装し、値の等価性を既定の動作が変更されたときに、多くの開発者が驚かれるでしょう。 します。  
  
 不変性をより参照の等価性と値の等価性の間の違いに注意をはるかに困難になるために、変更できない参照型の場合この問題が軽減されます。  
  
 **X 回避** が実装の参照の等価性の場合よりも大幅に遅れる場合は、参照型で等値演算子をオーバー ロードします。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)