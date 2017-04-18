---
title: "パス ファイル アクセス エラー |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
dev_langs:
- VB
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ac730bac76540331206daebe600445ca54cc15a9
ms.lasthandoff: 03/13/2017

---
# <a name="pathfile-access-error"></a>パス/ファイル アクセス エラー
ファイル アクセス、またはディスクへのアクセスの操作中に、オペレーティング システムは、パスとファイル名の間の接続を作成できませんでした。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  ファイルの仕様の書式が正しいことを確認します。 ファイル名は、完全修飾 (絶対値) または相対パスを含めることのパス。 (パスが別のドライブ上にある場合)、ドライブ名で完全修飾パスを開始し、明示的なルートからファイルへのパスを一覧表示します。 完全修飾されていない任意のパスでは、現在のドライブとディレクトリに対して相対的です。  
  
2.  既存の読み取り専用ファイルを置き換えるファイルの保存試みなかったことを確認します。 大文字と小文字の場合は、ターゲット ファイルの読み取り専用属性を変更または別のファイル名、ファイルを保存します。  
  
3.  シーケンシャルに読み取り専用ファイルを開く試みなかったかどうかを確認`Output`または`Append`モードです。 大文字と小文字の場合でファイルを開きます`Input`モードまたはファイルの読み取り専用属性を変更します。  
  
4.  変更しようとしてしなかったことを確認、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データベースまたはドキュメント内のプロジェクトです。  
  
## <a name="see-also"></a>関連項目  
 [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)
