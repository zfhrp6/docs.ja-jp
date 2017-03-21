---
title: "Sub または Function (Visual Basic) を定義されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d32bc9c8f13b245e6333c4460cab541f6e9409e
ms.lasthandoff: 03/13/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub または Function が定義されていません。(Visual Basic)
A`Sub`または`Function`呼び出せるために定義する必要があります。 このエラーでは以下の原因が考えられます。  
  
-   プロシージャ名のスペルが間違っています。  
  
-   別のプロジェクトでそのプロジェクトへの参照を明示的に追加することがなく、プロシージャを呼び出そうとしている、**参照** ダイアログ ボックス。  
  
-   呼び出し元のプロシージャには表示されないプロシージャを指定します。  
  
-   Windows ダイナミック リンク ライブラリ (DLL) のルーチンまたは指定したライブラリまたはコードのリソースに含まれていない Macintosh コード リソース ルーチンを宣言します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  プロシージャ名のスペルが正しいことを確認します。  
  
2.  呼び出すには必要な手順を含むプロジェクトの名前を検索、**参照** ダイアログ ボックス。 表示されない場合は、クリックして、**参照**を検索 ボタンをクリックします。 プロジェクト名の左側にチェック ボックスを選択し、クリックして**OK**します。  
  
3.  ルーチンの名前を確認してください。  
  
## <a name="see-also"></a>関連項目  
 [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
