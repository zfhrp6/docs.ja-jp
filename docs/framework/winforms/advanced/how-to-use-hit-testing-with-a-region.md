---
title: '方法 : 領域でヒット テストを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 40297fada3d042aee8c317eb787de03662f86cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523088"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>方法 : 領域でヒット テストを使用する
ヒット テストの目的では、カーソルをアイコンやボタンなどの特定のオブジェクト上にあるかどうかを決定します。  
  
## <a name="example"></a>例  
 次の例では、2 つの四角形領域の和集合を形成する、十字型の領域を作成します。 あると想定変数`point`最新のクリックの位置を保持します。 コードを確認するかどうか`point`が十字型領域内にします。 場合は、ポイントは、地域 (ヒット) では、不透明な赤いブラシ、地域が格納されます。 それ以外の場合、地域半透明の赤いブラシが格納されます。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Region>  
 [GDI+ での領域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [方法: 領域でクリッピングを使用する](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
