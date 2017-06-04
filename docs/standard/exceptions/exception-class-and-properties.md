---
title: "Exception クラスとプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "例外クラス"
  - "例外, 例外クラス"
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Exception クラスとプロパティ
<xref:System.Exception> クラスは、例外の継承元である基本クラスです。  ほとんどの例外オブジェクトは、**Exception** の派生クラスのインスタンスです。ただし、<xref:System.Object> クラスから派生したオブジェクトも例外としてスローできます。  一部の言語では、**Exception** の派生オブジェクト以外のオブジェクトのスロー操作とキャッチ操作がサポートされていません。  ほとんどの場合には、**Exception** オブジェクトだけをスローおよびキャッチすることをお勧めします。  
  
 **Exception** クラスには、例外を理解するときに役立つプロパティがいくつかあります。  このようなプロパティを次に示します。  
  
-   <xref:System.Exception.StackTrace%2A> プロパティ。  
  
     このプロパティにはスタック トレースが格納されています。エラーが発生した位置を判別するときに、このスタック トレースを使用できます。  デバッグ情報が使用できる場合には、スタック トレースにソース ファイル名とプログラム行番号が記述されます。  
  
-   <xref:System.Exception.InnerException%2A> プロパティ。  
  
     このプロパティによって、例外処理中に一連の例外が作成および保持されます。  また、既にキャッチされた例外を格納する新しい例外を作成するときにもこのプロパティを使用できます。  最初に発生した例外を、**InnerException** プロパティで作成された 2 番目の例外によって捕捉できるため、2 番目の例外を処理するコードが追加情報をチェックできます。  
  
     たとえば、ファイルを読み込み、データの書式を設定するメソッドがあるとします。  このメソッドのコードがファイルを読み込もうとしたときに、FileException がスローされたとします。  メソッドは FileException をキャッチし、BadFormatException をスローします。  この場合は、FileException を BadFormatException の **InnerException** プロパティに保存できます。  
  
     例外がスローされた原因を判別する呼び出し元の判別機能を向上させるには、ヘルパー ルーチンがスローした例外をキャッチしてから発生したエラーを詳しく示す例外をスローするメソッドを使用します。  エラーを詳しく示す例外を新規に作成して、最初に発生した例外に対して内部例外参照を設定できます。  次に、このエラーを詳しく示す例外を呼び出し元にスローできます。  この機能により、最初にスローされた例外で終了する、一連のリンクされた例外を作成できます。  
  
-   <xref:System.Exception.Message%2A> プロパティ。  
  
     このプロパティは、例外の原因に関する詳細情報を提供します。  **Message** は、例外をスローしたスレッドの <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=fullName> プロパティで指定された言語で表示されます。  
  
-   <xref:System.Exception.HelpLink%2A> プロパティ。  
  
     このプロパティは、例外の原因に関する詳細情報が記述されたヘルプ ファイルの URL \(または URN\) を保持します。  
  
-   <xref:System.Exception.Data%2A> プロパティ  
  
     このプロパティは、キーと値のペア内に任意のデータを保持できる IDictionary です。  
  
 **Exception** の継承クラスのほとんどは **Exception** を継承するだけであり、追加メンバーを実装せず、追加機能も提供しません。  したがって、例外に関する最も重要な情報は、例外の階層、例外名、および例外に格納されている情報から得られます。  
  
## 参照  
 [例外階層](../../../docs/standard/exceptions/exception-hierarchy.md)   
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [例外の推奨事項](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外](../../../docs/standard/exceptions/index.md)