---
title: 配列の上下限を、型指定子に記述できません。
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770f86ca960110965b6917a22d284678ff8b6f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>配列の上下限を、型指定子に記述できません。
配列サイズは、データ型の指定子の一部として宣言することはできません。  
  
 **エラー ID:** BC30638  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   次の例で示すように、型の後に、配列のサイズをかける代わりに変数名のすぐ後の配列のサイズを指定します。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   配列を定義し、次の例で示すように必要な数の要素を初期化します。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
