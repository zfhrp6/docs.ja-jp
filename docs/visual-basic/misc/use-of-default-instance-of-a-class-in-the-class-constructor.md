---
title: "クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a0c54c6e62f9bdc7fe510500a486461d26636d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>クラス コンストラクター内のクラスの既定のインスタンスを使用すると、無限の再帰呼び出しを引き起こす能性があります。
クラスの既定のインスタンスは、クラス コンストラクターで使用されています。 これは、無限ループとも呼ばれる、無限の再帰呼び出しを引き起こす可能性があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   クラス コンストラクターから、既定のインスタンスを削除します。  
  
## <a name="see-also"></a>関連項目  
 [コンストラクター](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
