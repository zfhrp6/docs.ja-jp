---
title: "My.Forms および My.WebServices が提供する既定のオブジェクト インスタンス (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44265c3f6f38a001192a8d92f2fbb6edeaca21cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms および My.WebServices が提供する既定のオブジェクト インスタンス (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)と[My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)オブジェクトは、フォーム、データ ソース、およびアプリケーションによって使用される XML Web サービスへのアクセスを提供します。 このように設定のコレクションを提供することによって*既定インスタンス*のこれらの各オブジェクトです。  
  
## <a name="default-instances"></a>既定のインスタンス  
 既定のインスタンスは、ランタイムによって提供されする必要がないクラスのインスタンスは、宣言およびインスタンスを使用して、`Dim`と`New`ステートメントです。 次の例は、どのようにする場合がありますが宣言およびインスタンスのインスタンス、<xref:System.Windows.Forms.Form>と呼ばれるクラス`Form1`、され、どのようにこれの既定のインスタンスを取得することが今すぐ<xref:System.Windows.Forms.Form>クラスを通じて`My.Forms`です。  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 `My.Forms`オブジェクトに対する既定のインスタンスのコレクションを返しますすべて`Form`プロジェクトに存在するクラス。 同様に、`My.WebServices`アプリケーションでへの参照を作成したすべての Web サービスのプロキシ クラスの既定のインスタンスを提供します。  
  
## <a name="see-also"></a>関連項目  
 [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [プロジェクトの種類に応じた My の機能](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
