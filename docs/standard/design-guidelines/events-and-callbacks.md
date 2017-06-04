---
title: "イベントとコールバック | Microsoft Docs"
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
  - "機能拡張のイベント [.NET Framework]"
  - "メソッド [.NET Framework], コールバック"
  - "コールバック メソッド"
  - "コールバック"
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# イベントとコールバック
コールバックはするがデリゲートからユーザー コードにコールバックするためのフレームワーク機能拡張ポイントです。 これらのデリゲートは、メソッドのパラメーターを通じて通常フレームワークに渡されます。  
  
 イベントは、コールバックのデリゲート \(イベント ハンドラー\) を提供するための便利で一貫した構文をサポートする特殊なケースです。 さらに、Visual Studio のステートメント入力候補および設計者は、イベント ベースの Api を使用してヘルプを提供します。 \(「[イベントのデザイン](../../../docs/standard/design-guidelines/event.md)」を参照\)。  
  
 **✓ を検討してください** コールバックを使用して、フレームワークによって実行されるカスタム コードを提供できるようにします。  
  
 **✓ を検討してください** イベントを使用したオブジェクト指向設計を理解することがなくても、フレームワークの動作をカスタマイズできるようにします。  
  
 **✓ は** 、広い範囲の開発者になじみのある、ステートメント入力候補の Visual Studio に統合されているために、イベントを単純なコールバックよりも優先されます。  
  
 **X 回避** パフォーマンスが重視される Api でコールバックを使用します。  
  
 **✓ は** 新しい `Func<...>`, 、`Action<...>`, 、または `Expression<...>` になったコールバック Api を定義するときに、カスタム デリゲートではなく型です。  
  
 `Func<...>` `Action<...>` 汎用デリゲートを表します。`Expression<...>` コンパイルして、後でも呼び出すことができますが、実行時にできる表します関数定義シリアル化およびリモート プロセスに渡されます。  
  
 **✓ は** を測定し、使用するパフォーマンスの影響について理解する `Expression<...>`, 、使用する代わりに `Func<...>` と `Action<...>` デリゲート。  
  
 `Expression<...>` ほとんどの場合と同じ論理的には種類が `Func<...>` と `Action<...>` デリゲート。 主な違いは、デリゲートがローカル処理のシナリオで使用するものであります。式は有益なリモート プロセスまたはコンピューターで式を評価するが適しています。  
  
 **✓ は** デリゲートを呼び出すことによって任意のコードを実行するかを理解し、セキュリティ、正確性、および互換性の影響を与える可能性です。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)