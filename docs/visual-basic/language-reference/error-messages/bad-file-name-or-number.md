---
title: ファイル名または番号が正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585568"
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
