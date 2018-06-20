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
# <a name="display-of-asian-characters-with-the-imemode-property"></a>ImeMode プロパティによるアジア言語の文字表示
<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティは、フォームとコントロールでは入力方式エディター (IME) の特定のモードを強制的に使用します。 IME は、日本語、中国語、韓国語のスクリプトを記述するために不可欠なコンポーネントです。これらの記述システムには、通常のキーボードではエンコードできない多くの文字があります。 たとえば、特定のテキスト ボックスで ASCII 文字のみを許可したい場合があります。 このようなケースで設定できます、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティを<xref:System.Windows.Forms.ImeMode>またユーザーはその特定のテキスト ボックスの ASCII 文字を入力することでのみです。 既定値、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティは<xref:System.Windows.Forms.ImeMode>ので、フォームのプロパティを設定すると、フォーム上のすべてのコントロールはその設定を継承します。 詳細については、次を参照してください。 <xref:System.Windows.Forms.Control.ImeMode%2A> ) と<xref:System.Windows.Forms.ImeMode>です。  
  
## <a name="see-also"></a>関連項目

[Windows フォーム アプリケーションのグローバル化](globalizing-windows-forms.md)
