---
title: "仮想メンバー | Microsoft Docs"
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
  - "オーバーライド可能なメンバー"
  - "仮想メンバー"
  - "仮想メンバー [.NET Framework]"
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 仮想メンバー
このため、サブクラスの動作を変更する、仮想メンバーをオーバーライドできます。 それらはそれらのもたらす拡張性の観点からのコールバックとよく似ていますが、実行のパフォーマンスとメモリの消費に関して優れています。 また、仮想メンバーは、特別な既存の型 \(特殊化\) の種類を作成する必要のあるシナリオで複数な操作です。  
  
 仮想メンバーは、コールバックとイベントよりパフォーマンスが向上は、非仮想メソッドをより実行はされません。  
  
 仮想メンバーの主な短所は、仮想メンバーの動作はコンパイル時にのみ変更できます。 コールバックの動作は、実行時に変更できます。  
  
 コールバック \(とそれよりコールバックの他の情報\) などの仮想メンバーは、設計、テスト、および仮想メンバーへの呼び出しが予測できない方法でオーバーライドされることができ、任意のコードを実行できるためのメンテナンス コストがかかる。 またより多くの労力は通常、設計およびそれらを文書化のコストが高いために、仮想メンバーの契約を明確に定義する要求されます。  
  
 **X のしないで** メンバーをそのためには相応の理由があり、設計、テスト、および仮想メンバーの保守に関連するすべてのコストを認識している場合を除き、仮想化します。  
  
 仮想メンバーは、変更を行う際に互換性を損なうことがなくに関して厳格に構成します。 また、これらは非仮想メンバーよりも低速仮想メンバーへの呼び出しがインライン関数ではないためにほとんどの場合です。  
  
 **✓ を検討してください** に何がどうしても必要なだけの機能拡張を制限することです。  
  
 **✓ は** 仮想メンバーのアクセシビリティは public で保護されたアクセシビリティを使用します。 パブリック メンバーが利用拡張 \(必要な場合\) プロテクト仮想メンバーを呼び出すことによってできます。  
  
 クラスのパブリック メンバーは、そのクラスの直接のコンシューマー向けの機能の適切なセットを提供する必要があります。 仮想メンバーが、サブクラスで無効にするように設計し、保護されたアクセシビリティがスコープを使用する場所へのすべての仮想機能拡張ポイントを有効にします。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)