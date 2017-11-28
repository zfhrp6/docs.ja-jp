---
title: "方法: XAML で特殊文字を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 308b2152f98286ba532a15e5491b5d1a25aa66dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a>方法: XAML で特殊文字を使用する
マークアップ ファイル内に作成される[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]で自動的に保存、 [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] utf-8 ファイル形式は、アクセント記号などのほとんどの特殊文字を正しくエンコードすることを意味します。 ただし、一般的に使用される一連の特殊文字で、別の方法で処理されるものがあります。 これらの特殊文字に従って、 [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]のエンコード標準です。  
  
 この一連の特殊文字をエンコードするための構文を次の表に示します。  
  
|文字|構文|説明|  
|---------------|------------|-----------------|  
|<|`<`|より小さい記号|  
|>|`>`|より大きい記号|  
|&|`&`|アンパサンド記号|  
|"|`"`|二重引用符記号|  
  
> [!NOTE]
>  作成する場合、テキストを使用するマークアップ ファイル エディターなど[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]メモ帳でファイルを保存する必要があります、[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]は保持するために utf-8 ファイル形式は、特殊文字をエンコードします。  
  
 次の例では、マークアップを作成するときにテキストで特殊文字を使用する方法を示します。  
  
## <a name="example"></a>例  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
