---
title: "クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6528ceabeb7fb7a1cdc0beff2fd362632a0a0c9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a>クラスがオートメーションをサポートしていないか、必要なインターフェイスをサポートしていません。
`GetObject` 関数呼び出しまたは `CreateObject` 関数呼び出しで指定したクラスが外部からプログラム可能なインターフェイスを公開していません。あるいは、.dll から .exe へ、または .exe から .dll へプロジェクトを変更しました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  オブジェクトを作成したアプリケーションのドキュメントを参照して、このクラスのオブジェクトでオートメーションを使用する上での制限を確認します。  
  
2.  .dll から .exe へ、または .exe から .dll へプロジェクトを変更した場合は、古い .dll または .exe を手動で登録解除する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [エラーの種類](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [ご意見](/visualstudio/ide/talk-to-us)
