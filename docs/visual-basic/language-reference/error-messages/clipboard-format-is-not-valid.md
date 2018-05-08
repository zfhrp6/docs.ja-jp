---
title: クリップボードの形式が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="clipboard-format-is-not-valid"></a>クリップボードの形式が有効ではありません。
指定されたクリップボードの形式は、実行中のメソッドと互換性がありません。 このエラーの考えられる原因には。  
  
-   クリップボードを使用して`GetText`または`SetText`メソッド以外のクリップボード形式を`vbCFText`または`vbCFLink`です。  
  
-   クリップボードを使用して`GetData`または`SetData`メソッド以外のクリップボード形式を`vbCFBitmap`、 `vbCFDIB`、または`vbCFMetafile`です。  
  
-   使用して、`DataObject``GetData`メソッドまたは`SetData`登録されている形式 (& HC000 - & HFFFF)、Microsoft Windows によって予約されている範囲内でのクリップボード形式を持つメソッドとそのクリップボードの形式が登録されていない Microsoft Windows と一緒にします。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   無効な形式を削除し、有効なものを指定します。  
  
## <a name="see-also"></a>関連項目  
 [クリップボード: その他のデータ形式の追加](/cpp/mfc/clipboard-adding-other-formats)
