---
title: "方法 : ユーザー定義の例外を作成する | Microsoft Docs"
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
  - "例外, 例"
  - "例外, ユーザー定義"
  - "ユーザー定義例外"
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : ユーザー定義の例外を作成する
ユーザーがプログラムによってエラー条件を識別できるようにする場合は、独自のユーザー定義例外を作成できます。  .NET Framework には、<xref:System.Exception> 基本クラスから最終的に派生した例外クラスの階層があります。  各クラスによって特定の例外が定義されているため、多くの場合は例外を作成する必要はありません。  <xref:System.Exception> クラスの派生クラスを独自の例外クラスとして作成することもできます。  
  
 独自の例外を作成するときには、ユーザー定義例外のクラス名の終わりに "Exception" という単語を付けておくと、コーディングの点で便利です。また、推奨される 3 つの共通コンストラクターを実装すると便利です。この推奨コンストラクターを実装する例を次に示します。  
  
> [!NOTE]
>  リモート処理機能を使用する場合には、サーバー \(呼び出される側\) とクライアント \(プロキシ オブジェクトまたは呼び出し元\) がユーザー定義例外のメタデータを使用できるようにしてください。  たとえば、別のアプリケーション ドメインのメソッドを呼び出すコードは、リモート呼び出しによってスローされる例外が含まれているアセンブリを検出できる必要があります。  詳細については、「[例外処理の実施](../../../docs/standard/exceptions/best-practices-for-exceptions.md)」を参照してください。  
  
 次の例では、新しい例外クラス `EmployeeListNotFoundException` は <xref:System.Exception> から派生しています。  3 つのコンストラクターはクラスで定義されていて、それぞれ異なるパラメーターを使用します。  
  
## 使用例  
 [!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
 [!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
 [!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  
  
## 参照  
 [方法 : Try ブロックと Catch ブロックを使用して例外をキャッチする](../../../docs/standard/exceptions/how-to-use-the-try-catch-block-to-catch-exceptions.md)   
 [方法 : catch ブロックで特定の例外を使用する](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)   
 [例外の推奨事項](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)