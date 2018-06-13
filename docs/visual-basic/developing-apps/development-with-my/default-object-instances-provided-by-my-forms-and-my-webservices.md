---
title: My.Forms および My.WebServices が提供する既定のオブジェクト インスタンス (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 421995684201ec48d5e8aff9b0ed7640efd1e4b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582663"
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
