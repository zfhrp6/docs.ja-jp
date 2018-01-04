---
title: "方法 : Windows フォームの境界線を変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e977617f16ef882ad0dcfe1a96a6e8af73d2ae48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>方法 : Windows フォームの境界線を変更する
Windows フォームの外観や動作を決定する際にはさまざまな境界線スタイルを選択できます。 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを変更して、フォームのサイズ変更動作を制御できます。 また、<xref:System.Windows.Forms.Form.FormBorderStyle%2A> を設定すると、キャプション バーの表示方法や、キャプション バーに表示されるボタンを変更できます。 詳細については、「<xref:System.Windows.Forms.FormBorderStyle>」を参照してください。  
  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] では、このタスクに対する広範なサポートが用意されています。  
  
 関連項目[する方法: デザイナーを使用して Windows フォームの境界線を変更](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\))です。  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>プログラムで Windows フォームの境界線スタイルを設定するには  
  
-   <xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを任意のスタイルに設定します。 次のコード例は、フォームの境界線スタイルを設定`DlgBx1`に<xref:System.Windows.Forms.FormBorderStyle.FixedDialog>です。  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     参照してください[する方法: デザイン時にダイアログ ボックスを作成する](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))です。  
  
     さらに、オプションを提供するフォームの境界線のスタイルを選択したかどうか**最小化**と**最大化**ボタン、これらのボタンを機能させるのには、どちらもをするかどうか指定できます。 これらのボタンは、ユーザーの操作感を細かく調節する場合に便利です。 **最小化**と**最大化**既定では、ボタンが有効になっているし、その機能を使用して操作が、**プロパティ**ウィンドウです。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [Windows フォームについて](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
