---
title: レコード番号が正しくありません
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be04987353498775ec7dcef50b6acc1e6b4ec149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="bad-record-number"></a>レコード番号が正しくありません
`a FileGet`、 `FilePut`、 `FileGetObject`、または `FilePutObject` ステートメント内のレコード番号が 0 以下です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  レコード番号の生成で使用される計算を確認します。 レコード番号が含まれている変数、またはレコード番号の計算で使用される変数のスペルを確認します。 モジュールで `Option Explicit On` を使用しない限り、スペル ミスの変数名は暗黙的に宣言され、0 に初期化されます。  
  
## <a name="see-also"></a>関連項目  
 [Option Explicit ステートメント](../../visual-basic/language-reference/statements/option-explicit-statement.md)
