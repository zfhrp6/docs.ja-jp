---
title: "抽象クラスのデザイン | Microsoft Docs"
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
  - "デザインのガイドラインを入力、抽象クラス"
  - "抽象クラスのデザイン ガイドライン"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] クラス"
  - "抽象クラス [.NET Framework]"
  - "クラス [.NET Framework] のデザイン ガイドライン"
  - "クラス型の設計ガイドライン"
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 抽象クラスのデザイン
**X のしないで** 抽象型のパブリックまたはプロテクトの内部コンス トラクターを定義します。  
  
 コンス トラクターは、ユーザーが型のインスタンスを作成する必要がある場合にのみ、パブリックにする必要があります。 抽象型のインスタンスを作成することはできませんのでパブリック コンス トラクターを持つ抽象型が正しくされていないに設計され、ユーザーに誤解を招きやすい。  
  
 **✓ は** 抽象クラス内で、保護されているか、内部コンス トラクターを定義します。  
  
 プロテクト コンス トラクターはより一般的なでき、単にサブタイプが作成されるときは、自己の初期化を実行する基本クラスです。  
  
 クラスを定義するアセンブリを抽象クラスの具象実装を制限するため、内部コンス トラクターを使用できます。  
  
 **✓ は** を出荷するそれぞれの抽象クラスから継承する少なくとも 1 つの具象型を提供します。  
  
 これにより、抽象クラスの設計を検証します。 たとえば、  <xref:System.IO.FileStream?displayProperty=fullName> の実装には、 <xref:System.IO.Stream?displayProperty=fullName> 抽象クラスです。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)