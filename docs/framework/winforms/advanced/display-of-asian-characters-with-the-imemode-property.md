---
title: "ImeMode プロパティによるアジア言語の文字表示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971fd9a75f936d2ec63eea6a086c681ec996652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>ImeMode プロパティによるアジア言語の文字表示
<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティは、フォームとコントロールでは入力方式エディター (IME) の特定のモードを強制的に使用します。 IME は、日本語、中国語、韓国語のスクリプトを記述するために不可欠なコンポーネントです。これらの記述システムには、通常のキーボードではエンコードできない多くの文字があります。 たとえば、特定のテキスト ボックスで ASCII 文字のみを許可したい場合があります。 このようなケースで設定できます、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティを<xref:System.Windows.Forms.ImeMode>またユーザーはその特定のテキスト ボックスの ASCII 文字を入力することでのみです。 既定値、<xref:System.Windows.Forms.Control.ImeMode%2A>プロパティは<xref:System.Windows.Forms.ImeMode>ので、フォームのプロパティを設定すると、フォーム上のすべてのコントロールはその設定を継承します。 詳細については、次を参照してください。 <xref:System.Windows.Forms.Control.ImeMode%2A> ) と<xref:System.Windows.Forms.ImeMode>です。  
  
## <a name="see-also"></a>参照  
 [Windows フォームのグローバル化](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
