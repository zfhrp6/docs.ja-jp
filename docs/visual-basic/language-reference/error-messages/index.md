---
title: "エラー メッセージ (Visual Basic) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 9f1cb93d5aaf7f90fc332594a2ca2a7cfc0c9c2f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="error-messages-visual-basic"></a>エラー メッセージ (Visual Basic)
Visual Basic アプリケーションを作成、コンパイル、実行する際は、次の種類のエラーが発生する可能性があります。  
  
1.  デザイン時エラー: Visual Studio でアプリケーションを作成するときに発生します。  
  
2.  コンパイル時エラー: Visual Studio またはコマンド プロンプトでアプリケーションをコンパイルするときに発生します。  
  
3.  実行時エラー: Visual Studio でアプリケーションまたはスタンドアロンの実行可能ファイルを実行するときに発生します。  
  
 特定のエラーのトラブルシューティング方法については、「[Visual Basic プログラマのための追加リソース](../../../visual-basic/getting-started/additional-resources.md)」を参照してください。  
  
## <a name="run-time-errors"></a>実行時エラー  
 Visual Basic アプリケーションがシステムで実行できないアクションを実行しようとすると、実行時エラーが発生し、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] によって `Exception` オブジェクトがスローされます。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では、`Throw` ステートメントを使用することで、`Exception` オブジェクトを含む任意のデータ型のカスタム エラーを生成できます。 アプリケーションは、キャッチされた例外のエラー番号とメッセージを表示して、エラーを識別できます。 エラーがキャッチされない場合、アプリケーションは終了します。  
  
 実行時エラーはコードでトラップして調べることができます。 エラーが発生するコードを `Try` ブロックで囲むと、スローされたエラーを対応する `Catch` ブロック内でキャッチできます。 実行時にエラーをトラップしてコードで対処する方法については、「[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
## <a name="compile-time-errors"></a>コンパイル時エラー  
 Visual Basic コンパイラがコード内で問題を検出すると、コンパイル時エラーが発生します。 コード エディターでは、エラーの原因となったコード行の下に波線が表示されるため、簡単にその行を特定できます。 波線をポイントするか**エラー一覧**を開くと、エラー メッセージが表示されます。エラー一覧には他のメッセージも表示されます。  
  
 識別子の下に波線があり、右端の文字の下に短い下線が表示されている場合は、クラス、コンストラクター、メソッド、プロパティ、フィールド、または列挙型のスタブを生成できます。 詳細については、「[Generate From Usage](https://docs.microsoft.com/visualstudio/ide/visual-csharp-intellisense#generate-from-usage)」(使用法から生成) を参照してください。
  
 Visual Basic コンパイラからのエラーを解決することにより、高速に実行されるバグの少ないコードを作成できます。 これらの警告では、アプリケーションの実行時にエラーを発生させるコードが示されます。 たとえば、ユーザーが、割り当てが行われていないオブジェクト変数のメンバーを呼び出そうとしたり、戻り値を設定せずに関数から戻ろうとしたり、例外をキャッチするロジックにエラーがある `Try` ブロックを実行しようとしたりすると、コンパイラは警告を表示します。 警告の表示/非表示を切り替える方法など、警告の詳細については、「[Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。

