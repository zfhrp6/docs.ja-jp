---
title: ファイルにこれ以上データがありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: abd5f5c6e5df262d1deadd74f0a146a8d436ceb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586742"
---
# <a name="input-past-end-of-file"></a>ファイルにこれ以上データがありません。
いずれか、`Input`ステートメントは、空であるファイルまたはすべてのデータを使用すると、またはを使用して 1 つから読み取っている、`EOF`ファイルを使用して関数がバイナリ用に開かれています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  使用して、`EOF`関数の直前に、`Input`ステートメント ファイルの終わりを検出します。  
  
2.  ファイルがバイナリ アクセスで開かれている場合を使用して`Seek`と`Loc`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
