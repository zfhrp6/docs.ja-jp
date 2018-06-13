---
title: パス ファイル アクセス エラー
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 83ce8615b173a6f5835347ebc561a793655ec8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598584"
---
# <a name="pathfile-access-error"></a>パス/ファイル アクセス エラー
ファイル アクセスまたはディスク アクセスの操作中に、オペレーティング システムは、パスとファイル名の間の接続を作成できませんでした。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  ファイルの仕様が正しく書式設定を確認します。 ファイル名は、完全修飾 (絶対値) または相対パスを含めることのパス。 (パスは、別のドライブ上にある) 場合、ドライブ名で完全修飾パスを開始し、明示的なルートからファイルへのパスを一覧表示します。 完全修飾されていない任意のパスでは、現在のドライブとディレクトリに対して相対的です。  
  
2.  既存の読み取り専用ファイルを置き換えると、ファイルを保存試みなかったを確認します。 大文字と小文字の場合は、ターゲット ファイルの読み取り専用属性を変更または別のファイル名を持つファイルを保存します。  
  
3.  シーケンシャルで読み取り専用ファイルを開くしようとしてしなかったことを確認してください`Output`または`Append`モード。 大文字と小文字の場合でファイルを開く`Input`モードまたはファイルの読み取り専用属性を変更します。  
  
4.  データベースまたはドキュメント内の Visual Basic プロジェクトを変更しようとしてしなかったことを確認します。  
  
## <a name="see-also"></a>関連項目  
 [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)
