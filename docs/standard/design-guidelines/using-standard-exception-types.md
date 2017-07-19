---
title: "標準の例外の型を使用します。 | Microsoft Docs"
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
  - "標準の種類の例外をスロー"
  - "キャッチ (例外の)"
  - "例外のキャッチ"
  - "例外のスロー"
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# 標準の例外の型を使用します。
このセクションでは、フレームワークとその使用方法の詳細な情報によって提供される標準の例外について説明します。 一覧は完全ではではありません。 その他のフレームワークの例外の種類の使用状況の .NET Framework リファレンス ドキュメントを参照してください。  
  
## 例外と SystemException  
 **X のしないで** スロー <xref:System.Exception?displayProperty=fullName> または <xref:System.SystemException?displayProperty=fullName>です。  
  
 **X のしないで** キャッチ `System.Exception` または `System.SystemException` framework コードで再スローする場合を除き、します。  
  
 **X 回避** キャッチ `System.Exception` または `System.SystemException`, では、トップレベルの例外ハンドラーです。  
  
## ApplicationException  
 **X のしないで** スローまたはそれから派生 <xref:System.ApplicationException>します。  
  
## InvalidOperationException  
 **✓ は** スロー、 <xref:System.InvalidOperationException> オブジェクトが状態が適切である場合。  
  
## ArgumentException、ArgumentNullException、および ArgumentOutOfRangeException  
 **✓ は** スロー <xref:System.ArgumentException> または不正な引数がメンバーに渡された場合は、そのサブタイプのいずれかです。 該当する場合は、最派生例外の種類を選びます。  
  
 **✓ は** 設定、 `ParamName` プロパティのサブクラスのいずれかをスローするときに `ArgumentException`します。  
  
 このプロパティは、例外がスローされる原因となったパラメーターの名前を表します。 コンス トラクター オーバー ロードのいずれかを使用して、プロパティを設定できることに注意してください。  
  
 **✓ は** を使用して `value` プロパティ set アクセス操作子の暗黙の value パラメーターの名前。  
  
## NullReferenceException、IndexOutOfRangeException、およびです \(accessviolationexception\)  
 **X のしないで** 明示的または暗黙的にスローする、api で公開されている呼び出し可能 <xref:System.NullReferenceException>, 、<xref:System.AccessViolationException>, 、または <xref:System.IndexOutOfRangeException>です。 これらの例外は予約されているとおよびほとんどの場合は、バグを示す場合に、実行エンジンによってスローされます。  
  
 引数に、これらの例外がスローされないようにチェックを行います。 これらの例外をスローすることは、時間の経過と共に変わる可能性があるメソッドの実装の詳細を公開します。  
  
## StackOverflowException  
 **X のしないで** を明示的にスロー <xref:System.StackOverflowException>します。 CLR によってのみ、例外が明示的にスローする必要があります。  
  
 **X のしないで** キャッチ `StackOverflowException`します。  
  
 ほとんどでは、任意のスタック オーバーフローが存在する場合に整合性があるマネージ コードを記述することはできません。 CLR のアンマネージ部分一貫して任意のスタック オーバーフローから取り除くではなく移動を適切に定義された場所スタックがオーバーフローしたプローブを使用しています。  
  
## OutOfMemoryException  
 **X のしないで** を明示的にスロー <xref:System.OutOfMemoryException>します。 この例外では、CLR インフラストラクチャによってのみがスローされます。  
  
## ComException、SEHException、および ExecutionEngineException  
 **X のしないで** を明示的にスロー <xref:System.Runtime.InteropServices.COMException>,  、<xref:System.ExecutionEngineException>, 、および <xref:System.Runtime.InteropServices.SEHException>です。 これらの例外では、CLR インフラストラクチャによってのみがスローされます。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [例外のデザイン ガイドライン](../../../docs/standard/design-guidelines/exceptions.md)