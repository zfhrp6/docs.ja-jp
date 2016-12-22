---
title: "End Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.End"
  - "End"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "execution, ending"
  - "files, closing"
  - "End keyword, End statements"
  - "programs, quitting"
  - "code, exiting"
  - "program termination"
  - "End statement"
  - "execution, stopping"
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# End Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プログラムの実行を終了させます。  
  
## 構文  
  
```  
End  
```  
  
## 解説  
 `End` ステートメントをプロシージャの任意の場所に記述すると、アプリケーション全体の実行を強制終了できます。  `End` は `Open` ステートメントで開いたすべてのファイルを閉じ、アプリケーションのすべての変数を削除します。  オブジェクトへの参照を保持している他のプログラムおよび実行中のコードがなくなると、アプリケーションはすぐに終了します。  
  
> [!NOTE]
>  `End` ステートメントは、コードの実行を直ちに停止し、`Dispose` メソッドや `Finalize` メソッド、またはその他の Visual Basic コードを呼び出しません。  他のプログラムが保持しているオブジェクトへの参照は、無効になります。  `End` ステートメントが `Try` ブロックや `Catch` ブロックの内部で実行された場合、対応する `Finally` ブロックに制御が渡されることはありません。  
  
 `Stop` ステートメントはプログラムの実行を中断しますが、`End` ステートメントと異なり、コンパイル済みの実行可能ファイル \(.EXE\) の内部でない限り、ファイルを閉じたり、変数をクリアすることはありません。  
  
 `End` は開いているリソースの後処理を何も行わずにアプリケーションを終了させるため、使用する前にリソースを正しく閉じてみる必要があります。  たとえば、アプリケーションのフォームが 1 つでも開いている場合は、制御が `End` ステートメントに到達する前にフォームを閉じてください。  
  
 `End` の使用はできる限り控えて、すぐに停止する必要がある場合にのみ使用してください。  通常の方法 \([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) および [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)\) を使ってプロシージャを終了させれば、プロシージャを正しく閉じることができるだけでなく、正しく閉じるための処理を呼び出し元のコードに追加することもできます。  たとえば、コンソール アプリケーションの場合なら、`Main` プロシージャから `Return` を実行するだけです。  
  
> [!IMPORTANT]
>  `End` ステートメントは、<xref:System> 名前空間にある <xref:System.Environment> クラスの <xref:System.Environment.Exit%2A> メソッドを呼び出します。  <xref:System.Environment.Exit%2A> を使用するには、`UnmanagedCode` のアクセス許可が必要です。  アクセス許可がない場合は <xref:System.Security.SecurityException> エラーが発生します。  
  
 [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) に続けてキーワードを記述すると、該当するプロシージャまたはブロックの定義を終了するという意味になります。  たとえば、`End Function` であれば `Function` プロシージャの定義が終了します。  
  
## 使用例  
 ユーザーが要求した場合に `End` ステートメントを使用してコードの実行を終了させるコード例は、次のとおりです。  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## スマート デバイス開発者のためのメモ  
 このステートメントはサポートされていません。  
  
## 参照  
 <xref:System.Security.Permissions.SecurityPermissionFlag>   
 [Stop Statement](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md)