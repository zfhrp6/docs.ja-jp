---
title: クリップボードの形式が有効ではありません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
