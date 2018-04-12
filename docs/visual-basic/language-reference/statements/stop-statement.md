---
title: Stop ステートメント (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b7f04214234837a86bf0c77c0d7b6934e2babd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="stop-statement-visual-basic"></a>Stop ステートメント (Visual Basic)
実行を中断します。  
  
## <a name="syntax"></a>構文  
  
```  
Stop  
```  
  
## <a name="remarks"></a>コメント  
 配置できる`Stop`ステートメントの実行を中断するプロシージャに任意の場所。 使用して、`Stop`ステートメントは、コードでブレークポイントの設定に似ています。  
  
 `Stop`ステートメントのとは異なりの実行が中断`End`、任意のファイルを閉じておよびコンパイル済み実行可能 (.exe) ファイルで検出された場合を除き、任意の変数をクリアされません。  
  
> [!NOTE]
>  場合、`Stop`ステートメントが、統合開発環境 (IDE) の外部で実行されているコードで発生した場合、デバッガーが呼び出されます。 これは、コードをデバッグまたはリテールのモードでコンパイルされたかどうかに関係なく当てはまります。  
  
## <a name="example"></a>例  
 この例では、`Stop`ステートメントの各繰り返しの実行を中断、`For...Next`ループします。  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
