---
title: "Error Messages (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "errors [Visual Basic]"
  - "error messages"
  - "trappable errors"
  - "errors [Visual Basic], trappable"
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Error Messages (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic アプリケーションを書き込むとき、コンパイルまたは実行すると、次の種類のエラーが発生することがあります:  
  
1.  Visual Studio のアプリケーションを作成すると生成されるデザイン時エラー。  
  
2.  Visual Studio のコマンド プロンプトまたはアプリケーションをコンパイルすると、コンパイル時のエラー。  
  
3.  Visual Studio のまたはスタンドアロン実行可能ファイルとしてアプリケーションを実行すると、実行時エラー。  
  
 特定のエラーをトラブルシューティングする方法の詳細については、[Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md)を参照してください。  
  
## ランタイム エラー  
 Visual Basic アプリケーションがシステムで処理できない動作を実行しようとすると、実行時エラーは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は `Exception` のオブジェクトに発生します。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、`Throw` ステートメントを使用することで、`Exception` オブジェクトを含む任意のデータ型のカスタム エラーを生成できます。  アプリケーションはキャッチされた例外の番号とメッセージを表示して、エラーを識別できます。  エラーがキャッチされない場合、アプリケーションは終了します。  
  
 コードは実行時エラーをトラップして確認できます。  `Try` ブロックのエラーを生成するコードを囲む、`Catch` の対応するブロック内でスローされたエラーを検出できます。  エラーを実行時に引っ掛け、コード内に応答する方法の詳細については、[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
## コンパイル時のエラー  
 Visual Basic コンパイラがコードの問題を検出すると、コンパイル エラーが発生します。  コード エディターで、波線がそのコード行表示される簡単にどのコード行でも、エラーが発生したかを特定できます。  エラー メッセージは、他のメッセージを示す波線の下線ポイントまたは **\[エラー一覧\]**を開くと表示されます。  
  
 識別子がの波線を持ち、短い下線が右端の文字の下に表示する場合、クラス、コンストラクター、メソッド、プロパティ、フィールド、または列挙型のスタブを生成できます。  詳細については、「[使用法から生成](/visual-cpp/misc/generate-from-usage)」を参照してください。  
  
 Visual Basic コンパイラの警告を解決して、高速に実行に発生するバグがあるコードを書き込むこともできます。  この警告は、アプリケーションの実行時にエラーが発生する可能性のあるコードを識別します。  たとえば、コンパイラは割り当てられていないオブジェクト変数のメンバーを呼び出そうとしたり、関数の戻り値を設定せずに戻るか、または例外をキャッチするロジックにエラーの `Try` のブロックを実行しようとすると、警告します。  警告に関する詳細については、含まれます。これらをオンまたはオフにする方法に [Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)を参照してください。