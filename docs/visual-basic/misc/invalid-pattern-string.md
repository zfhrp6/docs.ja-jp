---
title: "正しくないパターン文字列"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="invalid-pattern-string"></a>正しくないパターン文字列
検索の `Like` 演算で指定されているパターン文字列が正しくありません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  リスト式に使用できる文字を確認します。  
  
2.  パターン範囲の指定で、 `[a-z]`のように、範囲の開始文字が終了文字より小さいことを確認します。  
  
3.  パターン範囲の指定で、 `[a--z]`のように、複数のハイフンが続けて指定されていないことを確認します。  
  
4.  パターン範囲を右角かっこで終了します。  
  
## <a name="see-also"></a>関連項目  
 [Like 演算子](../../visual-basic/language-reference/operators/like-operator.md)
