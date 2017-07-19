---
title: "プロテクト メンバー | Microsoft Docs"
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
  - "保護されているメンバー [.NET Framework]"
  - "プロテクト メンバー"
  - "クラス [.NET Framework] の封印されていません。"
  - "メンバーの保護されているクラス [.NET Framework]"
  - "封印されていないクラス"
  - "クラスの動作をカスタマイズします。"
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# プロテクト メンバー
単独でプロテクト メンバーは、すべての機能拡張を指定しないが、高い拡張性により、サブクラス化をより強力なことができます。 メインのパブリック インターフェイスを不必要に複雑にせず、高度なカスタマイズ オプションを公開する、使用できます。  
  
 フレームワークの設計者は、「保護」の名前は、セキュリティに関する誤った認識を移すことができるため、保護されたメンバーには注意する必要があります。 サブクラス封印されていないクラスとメンバーへのアクセスが保護することがすべてのユーザーと、防御的なコーディング手法がパブリック メンバーを使用をプロテクト メンバーに適用するため、同じ。  
  
 **✓ を検討してください** プロテクト メンバーは高度なカスタマイズを使用します。  
  
 **✓ は** セキュリティ、ドキュメント、および互換性の分析を行うための public と封印されていないクラスでプロテクト メンバーを処理します。  
  
 クラスから継承するすべてのユーザーと、プロテクト メンバーにアクセスします。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)