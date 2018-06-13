---
title: '方法 : コントロールに透明な背景を指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: ad814c9179fd33955fe4df2666f8a47606bfbff0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531818"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="1bcaf-102">方法 : コントロールに透明な背景を指定する</span><span class="sxs-lookup"><span data-stu-id="1bcaf-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="1bcaf-103">.NET Framework の従来のバージョンでは、あらかじめフォームのコンストラクターに <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを設定しておかないと、透明な背景色を設定できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1bcaf-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="1bcaf-104">フレームワークの現在のバージョンでは、ほとんどのコントロールの背景色を、設計時に <xref:System.Drawing.Color.Transparent%2A> [プロパティ] **ウィンドウで、またはフォームのコンストラクターのコードで、** に設定できます。</span><span class="sxs-lookup"><span data-stu-id="1bcaf-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bcaf-105">Windows フォーム コントロールは、完全な透過性はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1bcaf-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="1bcaf-106">透明な Windows フォーム コントロールの背景は、その親によって描画されます。</span><span class="sxs-lookup"><span data-stu-id="1bcaf-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bcaf-107"><xref:System.Windows.Controls.Button> プロパティが <xref:System.Windows.Forms.ButtonBase.BackColor%2A> に設定されている場合でも、 <xref:System.Drawing.Color.Transparent%2A>コントロールは透明な背景をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="1bcaf-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="1bcaf-108">コントロールに透明な背景を設定するには</span><span class="sxs-lookup"><span data-stu-id="1bcaf-108">To give your control a transparent backcolor</span></span>  
  
-   <span data-ttu-id="1bcaf-109">[プロパティ] ウィンドウで <xref:System.Windows.Forms.ButtonBase.BackColor%2A> プロパティを選択し、 <xref:System.Drawing.Color.Transparent%2A>に設定します。</span><span class="sxs-lookup"><span data-stu-id="1bcaf-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcaf-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bcaf-110">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="1bcaf-111">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="1bcaf-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="1bcaf-112">マネージ グラフィックス クラスの使用</span><span class="sxs-lookup"><span data-stu-id="1bcaf-112">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [<span data-ttu-id="1bcaf-113">方法: 不透明な直線および半透明な直線を描画する</span><span class="sxs-lookup"><span data-stu-id="1bcaf-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
