---
title: ファイル名または番号が正しくありません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a>ファイル名または番号が正しくありません。
指定したファイルにアクセスしようとしているときにエラーが発生しました。 このエラーの考えられる原因には。  
  
-   ステートメントで指定されていないファイルの名前または番号のファイルを参照して、`FileOpen`で指定されたステートメントまたはを`FileOpen`ステートメントが、後で終了します。  
  
-   ステートメントは、ファイル番号の範囲外にある数値を持つファイルを参照します。  
  
-   ステートメントは、ファイル名または無効な数を表します。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  ファイル名がで指定されたことを確認してください、`FileOpen`ステートメントです。 呼び出した場合、`FileClose`ステートメント引数を指定せず可能性がありますが誤って閉じた開いているすべてのファイルです。  
  
2.  コードの生成は、ファイルの番号にアルゴリズムによっては場合、は、数値は有効なを確認します。  
  
3.  オペレーティング システムの規約に準拠しているかどうかを確認するファイルの名前を確認します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
