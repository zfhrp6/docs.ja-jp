---
title: '方法 : Windows フォームの NumericUpDown コントロールの書式を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 1cb8f8b7d2f86125736c08cd9eadf4eee30063bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533960"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="69890-102">方法 : Windows フォームの NumericUpDown コントロールの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="69890-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="69890-103">Windows フォームでの値を表示する方法を構成する<xref:System.Windows.Forms.NumericUpDown>コントロール。</span><span class="sxs-lookup"><span data-stu-id="69890-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="69890-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>プロパティ、小数点の後に表示される番号の数が以外の場合は、既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="69890-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="69890-105"><xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>プロパティは、3 桁ごと、区切り記号を挿入するかどうかを決定以外の場合は、既定値は`false`します。</span><span class="sxs-lookup"><span data-stu-id="69890-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="69890-106">コントロールは、場合に、10 進数の形式ではなく 16 進数の値を表示できます、<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>プロパティに設定されている`true`; 既定値は`false`します。</span><span class="sxs-lookup"><span data-stu-id="69890-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="69890-107">数値の値の書式設定</span><span class="sxs-lookup"><span data-stu-id="69890-107">To format the numeric value</span></span>  
  
-   <span data-ttu-id="69890-108">設定して、10 進値を表示、<xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>プロパティ整数と設定を<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>プロパティを`true`または`false`です。</span><span class="sxs-lookup"><span data-stu-id="69890-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     <span data-ttu-id="69890-109">- または -</span><span class="sxs-lookup"><span data-stu-id="69890-109">-or-</span></span>  
  
-   <span data-ttu-id="69890-110">16 進数の値を設定して表示、<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="69890-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="69890-111">値は、16 進数としてフォームに表示されて、場合でも他のテストを実行するには<xref:System.Windows.Forms.NumericUpDown.Value%2A>プロパティは、10 進値をテストします。</span><span class="sxs-lookup"><span data-stu-id="69890-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69890-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="69890-112">See Also</span></span>  
 <xref:System.Windows.Forms.NumericUpDown>  
 [<span data-ttu-id="69890-113">NumericUpDown コントロール</span><span class="sxs-lookup"><span data-stu-id="69890-113">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [<span data-ttu-id="69890-114">NumericUpDown コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="69890-114">NumericUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
