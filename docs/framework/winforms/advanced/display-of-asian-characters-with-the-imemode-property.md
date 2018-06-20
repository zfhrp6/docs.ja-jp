---
title: ImeMode プロパティによるアジア言語の文字表示
ms.date: 03/30/2017
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
ms.openlocfilehash: d3733f642d4218c851040582ee5637b5486a7804
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208629"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="bb752-102">ImeMode プロパティによるアジア言語の文字表示</span><span class="sxs-lookup"><span data-stu-id="bb752-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="bb752-103"><xref:System.Windows.Forms.Control.ImeMode%2A>プロパティは、フォームとコントロールでは入力方式エディター (IME) の特定のモードを強制的に使用します。</span><span class="sxs-lookup"><span data-stu-id="bb752-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="bb752-104">IME は、日本語、中国語、韓国語のスクリプトを記述するために不可欠なコンポーネントです。これらの記述システムには、通常のキーボードではエンコードできない多くの文字があります。</span><span class="sxs-lookup"><span data-stu-id="bb752-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="bb752-105">たとえば、特定のテキスト ボックスで ASCII 文字のみを許可したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb752-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="bb752-106">このようなケースで設定できます、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティを<xref:System.Windows.Forms.ImeMode>またユーザーはその特定のテキスト ボックスの ASCII 文字を入力することでのみです。</span><span class="sxs-lookup"><span data-stu-id="bb752-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="bb752-107">既定値、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティは<xref:System.Windows.Forms.ImeMode>ので、フォームのプロパティを設定すると、フォーム上のすべてのコントロールはその設定を継承します。</span><span class="sxs-lookup"><span data-stu-id="bb752-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="bb752-108">詳細については、次を参照してください。 <xref:System.Windows.Forms.Control.ImeMode%2A> ) と<xref:System.Windows.Forms.ImeMode>です。</span><span class="sxs-lookup"><span data-stu-id="bb752-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb752-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb752-109">See also</span></span>

[<span data-ttu-id="bb752-110">Windows フォーム アプリケーションのグローバル化</span><span class="sxs-lookup"><span data-stu-id="bb752-110">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
