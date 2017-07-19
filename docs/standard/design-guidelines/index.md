---
title: "Framework デザイン ガイドライン | Microsoft Docs"
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
  - ".NET Framework クラス ライブラリのライブラリ"
  - "クラス ライブラリ デザイン ガイドライン [.NET Framework]"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework]"
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Framework デザイン ガイドライン
このセクションでは、ライブラリを拡張し、.NET Framework と対話するをデザインのガイドラインを示します。 目標は、ライブラリの設計者が開発に使用するプログラミング言語とは独立統一されたプログラミング モデルを提供することにより、API の一貫性と使いやすさをことを確認のためです。 .NET Framework を拡張するクラスやコンポーネントを開発する際に、これらのデザイン ガイドラインに従うことをお勧めします。 一貫性のないライブラリ デザイン悪影響を及ぼす開発者の生産性に影響することはお導入します。  
  
 ガイドラインは、条件付け簡単な推奨方法として構成 `Do`, 、`Consider`, 、`Avoid`, 、および `Do not`です。 次のガイドラインは、さまざまなソリューション間のトレードオフを理解するクラス ライブラリのデザイナーを支援するものです。 優れたライブラリ デザインではこれらのデザイン ガイドラインに違反することが必要とする状況である可能性があります。 このような場合はまれと、明確で有利な決定の理由は、重要です。  
  
 次のガイドラインがの著書から抜粋した *Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリ \(第 2 版\) 用のパターン*, は Cwalina、Brad エイブラムスによるします。  
  
## このセクションの内容  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 アセンブリ、名前空間、型、およびクラス ライブラリ内のメンバーの名前付けのガイドラインを提供します。  
  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)  
 静的な抽象クラス、インターフェイス、列挙体、構造体、およびその他の種類を使用するためのガイドラインを提供します。  
  
 [メンバー デザインのガイドライン](../../../docs/standard/design-guidelines/member.md)  
 設計とプロパティ、メソッド、コンス トラクター、フィールド、イベント、演算子、およびパラメーターの使用に関するガイドラインを提供します。  
  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 イベントや仮想メンバーは、コールバック関数を使用して、サブクラス化などの機能拡張機構について説明し、フレームワークの要件に最適なメカニズムを選択する方法を説明します。  
  
 [例外のデザイン ガイドライン](../../../docs/standard/design-guidelines/exceptions.md)  
 デザイン、スロー、および例外をキャッチの設計ガイドラインについて説明します。  
  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 配列、属性、およびコレクションなどの一般的な型を使用して、シリアル化のサポート、等値演算子のオーバー ロードするためのガイドラインについて説明します。  
  
 [一般的な設計パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 選択して、依存関係プロパティと、dispose パターンを実装するためのガイドラインを提供します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [概要](../../../docs/framework/get-started/overview.md)   
 [.NET Framework のロードマップ](http://msdn.microsoft.com/ja-jp/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)   
 [開発ガイド](../../../docs/framework/development-guide.md)