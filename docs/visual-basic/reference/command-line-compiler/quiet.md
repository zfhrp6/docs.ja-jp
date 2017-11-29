---
title: /quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b816cadb9d805d57a14e9b5df553654dd8167af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="quiet"></a>/quiet
コンパイラで構文関連のエラーと警告のコードが表示されないようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/quiet  
```  
  
## <a name="remarks"></a>コメント  
 既定では、`/quiet` は無効です。 コンパイラは、構文に関連するエラーまたは警告を報告、したときにも、ソース コードから行を出力します。 コンパイラの出力を解析するアプリケーションでは、コンパイラで診断のテキストのみを出力する方が便利場合があります。  
  
 次の例では、`Module1`を含むソース コードなしでコンパイルされるときにエラーが出力`/quiet`です。  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 Output:  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 コンパイルされた`/quiet`コンパイラは次のオプションのみを出力します。  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  `/quiet`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`し、コードの構文に関連するコンパイラの診断情報を表示しません。  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
