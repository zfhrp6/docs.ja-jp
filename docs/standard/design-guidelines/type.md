---
title: "型デザインのガイドライン | Microsoft Docs"
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
  - "型デザインのガイドライン"
  - "型デザインのガイドラインについての型のデザイン ガイドライン"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] 型のデザインのガイドライン"
  - "型 [.NET Framework] のデザイン ガイドライン"
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 型デザインのガイドライン
CLR の観点からは、型の 2 つのカテゴリがあります: 参照型と値の型、型それぞれ独自の特定の設計規則に以上の論理グループに分割してフレームワーク デザインの詳細については、目的が、します。  
  
 クラスは、参照型の一般的なケースです。 ほとんどのフレームワークの型の大部分を構成します。 クラスは、サポートされる他のオブジェクト指向の機能の豊富なをし、一般的な適用性を的な人気を支払わなかったです。 基本クラスと抽象クラスは、拡張機能に関連する、特別な論理グループです。  
  
 インターフェイスは、参照型と値の型の両方によって実装可能な型の型です。 したがって、参照型と値の型のポリモーフィックな階層のルートとして使用することができます。 さらに、インターフェイスは、CLR によってネイティブでサポートされていない多重継承をシミュレートするために使用できます。  
  
 構造体は、値型の一般的な場合があり、小規模でシンプルな型、言語プリミティブのように予約されている必要があります。  
  
 列挙型は、日、週、コンソールの色のなどの値の短いセットを定義するのに使用される値型の特殊なケースです。  
  
 静的クラスは、型の静的メンバーのコンテナーを示すものです。 その他の操作へのショートカットを提供するよく使用されます。  
  
 デリゲート、例外、属性、配列、およびコレクションは、特別な用途のためのもので、参照型のすべての特殊なケースとの設計と使用法に関するガイドラインはこのドキュメントで他の場所で説明します。  
  
 **✓ は** 各タイプが適切に定義された一連の関連するメンバーは、ランダムな関連性のない機能のコレクションだけでなくであることを確認します。  
  
## このセクションの内容  
 [クラスまたは構造体の選択](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [抽象クラスのデザイン](../../../docs/standard/design-guidelines/abstract-class.md)  
 [静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)  
 [インターフェイスのデザイン](../../../docs/standard/design-guidelines/interface.md)  
 [構造体のデザイン](../../../docs/standard/design-guidelines/struct.md)  
 [列挙型デザイン](../../../docs/standard/design-guidelines/enum.md)  
 [入れ子にされた型](../../../docs/standard/design-guidelines/nested-types.md)  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)