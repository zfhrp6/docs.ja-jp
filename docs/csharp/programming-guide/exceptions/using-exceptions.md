---
title: "例外の使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外処理 [C#], 例外処理の概要"
  - "例外 [C#], 概要 (例外の)"
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 例外の使用 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# では、プログラムの実行時に発生したエラーは、例外という機能を通じてプログラムに伝えられます。  例外は、エラーが発生したコードによってスローされ、エラーを修正できるコードによってキャッチされます。  例外は、.NET Framework 共通言語ランタイム \(CLR: Common Language Runtime\) またはプログラムのコードによってスローできます。  スローされた例外は、例外の `catch` ステートメントが見つかるまで呼び出し履歴をさかのぼります。  キャッチされない例外は、システムが提供する汎用例外ハンドラーによって処理され、ダイアログ ボックスが表示されます。  
  
 例外は、<xref:System.Exception> から派生したクラスによって表されます。  このクラスは、例外の型を識別し、その例外に関する詳細情報を含むプロパティを保持します。  例外をスローするには、例外の派生クラスのインスタンスを作成し、必要に応じて例外のプロパティを設定してから、`throw` キーワードを使用してオブジェクトをスローします。  次に例を示します。  
  
 [!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 例外がスローされると、ランタイムは現在のステートメントが `try` ブロック内に存在するかどうかを確認します。  存在する場合は、`try` ブロックに関連付けられている `catch` ブロックが例外をキャッチできるかどうかを確認します。  通常は、この `Catch` ブロックによって例外の型が指定されます。`catch` ブロックの型と、例外または例外の基本クラスの型が一致する場合、`catch` ブロックはメソッドを処理できます。  次に例を示します。  
  
 [!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 例外をスローするステートメントが `try` ブロックに存在しない場合、またはステートメントを含む `try` ブロックに適合する `catch` ブロックが存在しない場合、ランタイムは、呼び出し側のメソッドで `try` ステートメントと `catch` ブロックを探します。  ランタイムは、呼び出し履歴を続けて、対応する `catch` ブロックを検索します。  `catch` ブロックが見つかり、実行されると、その `catch` ブロックの後にある次のステートメントに制御が渡されます。  
  
 `try` ステートメントには、複数の `catch` ブロックを含めることができます。  例外を処理できる最初の `catch` ステートメントが実行され、その後の `catch` ステートメントは、対応していても無視されます。  したがって、catch ブロックは、特定性の高いもの \(または最派生のもの\) から低いものに順番に配置する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 `catch` ブロックが実行される前に、ランタイムにより `finally` ブロックがチェックされます。  `Finally` ブロックにより、中止された `try` ブロックによって残されることがあるあいまいな状態をクリーンアップすること、またはランタイムのガベージ コレクターがオブジェクトを終了させるのを待たずに外部リソース \(グラフィック ハンドル、データベース接続、ファイル ストリームなど\) を解放することができます。  次に例を示します。  
  
 [!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 `WriteByte()` が例外をスローした場合は、`file.Close()` を呼び出さないと、ファイルを再度開こうとする 2 番目の `try` ブロックのコードは失敗し、ファイルはロックされたままになります。  `finally` ブロックは、例外がスローされても実行されるので、上の例の `finally` ブロックにより、ファイルを適切に閉じて、エラーを回避できます。  
  
 例外がスローされた後に、対応する `catch` ブロックが呼び出し履歴に見つからない場合は、次のいずれかが生じます。  
  
-   例外がデストラクターの内部で発生した場合、デストラクターは中止され、基本デストラクター \(存在する場合\) が呼び出されます。  
  
-   呼び出し履歴に静的コンストラクターまたは静的フィールド初期化子が含まれている場合、<xref:System.TypeInitializationException> がスローされ、この新しい例外の <xref:System.Exception.InnerException%2A> プロパティに元の例外が割り当てられます。  
  
-   スレッドの開始位置に到達すると、スレッドは終了します。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)