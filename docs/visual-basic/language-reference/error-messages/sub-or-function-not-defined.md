---
title: Sub または Function が定義されていません。(Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub または Function が定義されていません。(Visual Basic)
A`Sub`または`Function`呼び出すには定義する必要があります。 このエラーでは以下の原因が考えられます。  
  
-   プロシージャ名のスペルが間違っています。  
  
-   別のプロジェクトでそのプロジェクトへの参照を明示的に追加することがなく、プロシージャを呼び出そうとしている、**参照** ダイアログ ボックス。  
  
-   呼び出し元のプロシージャには表示されませんプロシージャを指定します。  
  
-   Windows ダイナミック リンク ライブラリ (DLL) のルーチンまたは指定したライブラリまたはコード リソースに含まれていない Macintosh コード リソース ルーチンを宣言します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  プロシージャ名のスペルが正しいことを確認します。  
  
2.  呼び出しに必要な手順を含むプロジェクトの名前を検索、**参照** ダイアログ ボックス。 表示されない場合にクリックして、**参照**検索ボタンをクリックします。 プロジェクト名の左側にチェック ボックスをオンにし、をクリックして**OK**です。  
  
3.  ルーチンの名前を確認してください。  
  
## <a name="see-also"></a>関連項目  
 [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
