---
title: "Error Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.error"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Error statement, syntax"
  - "Error statement"
  - "Error keyword"
  - "run-time errors, codes"
  - "errors [Visual Basic], simulating"
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Error Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

エラーの発生をシミュレートします。  
  
## 構文  
  
```  
Error errornumber  
```  
  
## 指定項目  
 `errornumber`  
 必ず指定します。  任意の有効なエラー番号を指定できます。  
  
## 解説  
 `Error` ステートメントは下位互換性用にサポートされています。  新しいコードでは、`Err` オブジェクトの `Raise` メソッドを使用してランタイム エラーを生成します。特に、オブジェクトを作成する場合はこのメソッドを使用します。  
  
 `errornumber` を定義すると、`Error` ステートメントは、`Err` オブジェクトのプロパティに次の表の既定値を割り当ててからエラー ハンドラーを呼び出します。  
  
|プロパティ|値|  
|-----------|-------|  
|`Number`|`Error` ステートメントの引数として指定される値。  任意の有効なエラー番号を指定できます。|  
|`Source`|現在の Visual Basic プロジェクトの名前。|  
|`Description`|この文字列が存在する場合は、指定の `Number` に対する `Error` 関数の戻り値に対応する文字列式。  文字列が存在しない場合、`Description` には長さ 0 の文字列 \(""\) が含まれます。|  
|`HelpFile`|適切な Visual Basic ヘルプ ファイルへの絶対的なドライブ、パス、およびファイル名。|  
|`HelpContext`|適切な Visual Basic ヘルプ ファイルの、`Number` プロパティに対応するエラーのコンテキスト ID。|  
|`LastDLLError`|ゼロ。|  
  
 エラー ハンドラーがないか、または有効でない場合は、`Err` オブジェクトのプロパティによってエラー メッセージが作成および表示されます。  
  
> [!NOTE]
>  一部の Visual Basic ホスト アプリケーションではオブジェクトを作成できません。  クラスやオブジェクトを作成できるかどうかを確認するには、ホスト アプリケーションのドキュメントを参照してください。  
  
## 使用例  
 `Error` ステートメントを使ってエラー番号 11 を生成する例を次に示します。  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## 必要条件  
 **名前空間**: [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ**: Visual Basic ランタイム ライブラリ \(Microsoft.VisualBasic.dll 内\)  
  
## 参照  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>   
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Error Messages](../../../visual-basic/language-reference/error-messages/index.md)