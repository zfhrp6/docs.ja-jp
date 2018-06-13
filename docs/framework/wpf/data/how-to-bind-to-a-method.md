---
title: '方法 : メソッドにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 58e243812f9c2dcb65dc37bfd50d9bcfb124e4f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557096"
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="7f88f-102">方法 : メソッドにバインドする</span><span class="sxs-lookup"><span data-stu-id="7f88f-102">How to: Bind to a Method</span></span>
<span data-ttu-id="7f88f-103">次の例を使用して、メソッドにバインドする方法を示しています。<xref:System.Windows.Data.ObjectDataProvider>です。</span><span class="sxs-lookup"><span data-stu-id="7f88f-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f88f-104">例</span><span class="sxs-lookup"><span data-stu-id="7f88f-104">Example</span></span>  
 <span data-ttu-id="7f88f-105">この例では、`TemperatureScale` はメソッド `ConvertTemp` を持つクラスで、2 つのパラメーター (1 つは `double` でもう 1 つは `enum` 型 `TempType)`) を取得して、指定した値をある温度尺度から他の温度尺度へ変換します。</span><span class="sxs-lookup"><span data-stu-id="7f88f-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="7f88f-106">次の例で、<xref:System.Windows.Data.ObjectDataProvider>インスタンスを作成するために使用、`TemperatureScale`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7f88f-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="7f88f-107">`ConvertTemp` メソッドは、2 つの指定したパラメーターで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7f88f-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="7f88f-108">このメソッドはリソースとして使用可能となり、その結果にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="7f88f-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="7f88f-109">次の例で、<xref:System.Windows.Controls.TextBox.Text%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>の<xref:System.Windows.Controls.ComboBox>メソッドの 2 つのパラメーターにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="7f88f-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="7f88f-110">これにより、ユーザーは、変換する温度と変換前の温度尺度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7f88f-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="7f88f-111">なお<xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>に設定されている`true`におをバインドするため、<xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A>のプロパティ、<xref:System.Windows.Data.ObjectDataProvider>インスタンスとによってラップされたオブジェクトのプロパティではありません、 <xref:System.Windows.Data.ObjectDataProvider> (、`TemperatureScale`オブジェクト)。</span><span class="sxs-lookup"><span data-stu-id="7f88f-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="7f88f-112"><xref:System.Windows.Controls.ContentControl.Content%2A> 、最後の<xref:System.Windows.Controls.Label>ユーザーのコンテンツを変更すると、更新、<xref:System.Windows.Controls.TextBox>または選択範囲の<xref:System.Windows.Controls.ComboBox>です。</span><span class="sxs-lookup"><span data-stu-id="7f88f-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="7f88f-113">コンバーター `DoubleToString` double 型の値を取得し、内の文字列に変換します、<xref:System.Windows.Data.IValueConverter.Convert%2A>方向 (はバインディング ターゲットに、バインディング ソースから、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティ) に変換し、`string`を、`double`で、 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 。方向です。</span><span class="sxs-lookup"><span data-stu-id="7f88f-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="7f88f-114">`InvalidationCharacterRule`は、<xref:System.Windows.Controls.ValidationRule>無効な文字のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7f88f-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="7f88f-115">赤い枠線では、既定のエラーのテンプレートの周囲、 <xref:System.Windows.Controls.TextBox>、入力値が double 値ではないときにユーザーに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7f88f-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f88f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f88f-116">See Also</span></span>  
 [<span data-ttu-id="7f88f-117">方法トピック</span><span class="sxs-lookup"><span data-stu-id="7f88f-117">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [<span data-ttu-id="7f88f-118">方法: 列挙値にバインドする</span><span class="sxs-lookup"><span data-stu-id="7f88f-118">Bind to an Enumeration</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
