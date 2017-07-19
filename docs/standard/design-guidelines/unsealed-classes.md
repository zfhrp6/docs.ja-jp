---
title: "封印されていないクラス | Microsoft Docs"
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
  - "クラス [.NET Framework] の封印されていません。"
  - "封印されていないクラス"
  - "クラスの継承"
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 封印されていないクラス
シール クラスは継承できませんし、機能拡張は、します。 これに対し、封印されていないクラスから継承できるクラスと呼びます。  
  
 **✓ を検討してください** 安価で提供する優れた方法まだ非常に役に立ちますフレームワークへの拡張機能として、仮想メンバーまたはプロテクト メンバーを追加なしで封印されていないクラスを使用します。  
  
 多くの場合、開発者はカスタム コンス トラクター、新しいメソッドは、メソッドのオーバー ロードなどのための便利なメンバーを追加するために封印されていないクラスから継承したいと考えているとします。 たとえば、  `System.Messaging.MessageQueue` が封印されていないと、できるので、ユーザーがその既定値を特定のキューのパスにカスタムのキューを作成する特定のシナリオ用の API を単純化するカスタム メソッドを追加します。  
  
 既定では、ほとんどのプログラミング言語でクラスが封印されていない、フレームワークのほとんどのクラスに対して推奨される既定ではもできます。 封印されていない型によって提供される拡張機能は、フレームワークのユーザーが非常にありがたいと封印されていない型に関連付けられた相対的に低いテスト コストによりを提供する非常に低価格です。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [封印](../../../docs/standard/design-guidelines/sealing.md)