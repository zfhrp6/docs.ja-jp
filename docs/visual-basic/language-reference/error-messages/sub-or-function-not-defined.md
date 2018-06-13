---
title: Sub または Function が定義されていません。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 58e90d769d5a7f2d88b5c27d1ec7d0d28c8d7b03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593702"
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
