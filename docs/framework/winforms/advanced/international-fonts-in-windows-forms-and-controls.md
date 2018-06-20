---
title: Windows フォームとコントロールの国際対応フォント
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: b2738f174c9837a2ba83c1306f4617f39ce17de1
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208601"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="a8250-102">Windows フォームとコントロールの国際対応フォント</span><span class="sxs-lookup"><span data-stu-id="a8250-102">International fonts in Windows Forms and controls</span></span>

<span data-ttu-id="a8250-103">国際対応のアプリケーションでは、可能な限り、フォント フォールバックを使用するフォントを選択する勧めします。</span><span class="sxs-lookup"><span data-stu-id="a8250-103">In International applications, the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="a8250-104">システムがどのようなスクリプトの文字を決定するフォント代替手段に属しています。</span><span class="sxs-lookup"><span data-stu-id="a8250-104">Font fallback means that the system determines what script the character belongs to.</span></span>

## <a name="using-font-fallback"></a><span data-ttu-id="a8250-105">フォント フォールバックの使用</span><span class="sxs-lookup"><span data-stu-id="a8250-105">Using font fallback</span></span>

<span data-ttu-id="a8250-106">この機能を利用するを設定しないで、<xref:System.Drawing.Font>フォームまたはその他の要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a8250-106">To take advantage of this feature, don't set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="a8250-107">アプリケーションでは、オペレーティング システムの 1 つのローカライズされた言語によって異なるため既定のシステム フォントが自動的に使用します。</span><span class="sxs-lookup"><span data-stu-id="a8250-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="a8250-108">アプリケーションを実行すると、システムは自動的に提供されているオペレーティング システムで選択したカルチャに適切なフォントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8250-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>

<span data-ttu-id="a8250-109">例外が発生しました、規則に、フォント、フォント スタイルを変更するために設定されていないのです。</span><span class="sxs-lookup"><span data-stu-id="a8250-109">There's an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="a8250-110">これは、ユーザーが太字で表示されるテキスト ボックス内のテキストを作成する場合、ボタンをクリックしたアプリケーションの重要なことがあります。</span><span class="sxs-lookup"><span data-stu-id="a8250-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="a8250-111">実行するには関数を作成する、太字で表示するテキスト ボックスのフォント スタイルを変更する、フォームのフォントにします。</span><span class="sxs-lookup"><span data-stu-id="a8250-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="a8250-112">2 つの場所でこの関数の呼び出しすることが重要: ボタンの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーと、<xref:System.Windows.Forms.Control.FontChanged>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="a8250-112">It's important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="a8250-113">のみ、関数が呼び出される場合、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーとコードの他のいくつかの部分は、フォーム全体のフォント ファミリを変更、テキスト ボックス、フォームの残りの部分では変更されません。</span><span class="sxs-lookup"><span data-stu-id="a8250-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box doesn't change with the rest of the form.</span></span>

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

<span data-ttu-id="a8250-114">ただし、アプリケーションをローカライズするときに太字のフォント可能性があります表示が不十分な特定の言語。</span><span class="sxs-lookup"><span data-stu-id="a8250-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="a8250-115">これに問題がある場合ローカライズで通常のテキストに太字のフォントを切り替えるオプションをします。</span><span class="sxs-lookup"><span data-stu-id="a8250-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="a8250-116">ローカライザーがない開発者は、通常、ソース コードへのアクセス権がないので、リソース ファイルにのみこのオプション必要があるリソース ファイルで設定します。</span><span class="sxs-lookup"><span data-stu-id="a8250-116">Since localizers are typically not developers and don't have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="a8250-117">これを行うには、設定すると、<xref:System.Drawing.Font.Bold%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="a8250-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="a8250-118">これは、結果、ローカライザーが編集できる、リソース ファイルに書き出され、フォントを設定します。</span><span class="sxs-lookup"><span data-stu-id="a8250-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="a8250-119">後にコードを作成し、`InitializeComponent`フォントを再設定する方法、フォームのフォントに基づいていますが、リソース ファイルで指定されたフォント スタイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8250-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a><span data-ttu-id="a8250-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8250-120">See also</span></span>

[<span data-ttu-id="a8250-121">Windows フォーム アプリケーションのグローバル化</span><span class="sxs-lookup"><span data-stu-id="a8250-121">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)  
[<span data-ttu-id="a8250-122">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="a8250-122">Using Fonts and Text</span></span>](using-fonts-and-text.md)