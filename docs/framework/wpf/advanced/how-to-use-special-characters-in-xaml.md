---
title: "方法 : XAML で特殊文字を使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字, 特殊"
  - "特殊文字"
  - "タイポグラフィ, 特殊文字"
  - "Unicode UTF-8 ファイル形式"
  - "UTF-8 ファイル形式"
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 方法 : XAML で特殊文字を使用する
[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] で作成されたマークアップ ファイルは、自動的に [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF\-8 ファイル形式で保存されます。つまり、アクセント マークなど、ほとんどの特殊文字が正しくエンコードされます。  ただし、一般的に使用される一連の特殊文字で、別の方法で処理されるものがあります。  これらの特殊文字は、エンコーディングに関する [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 標準に従います。  
  
 この一連の特殊文字をエンコードするための構文を次の表に示します。  
  
|文字|構文|Description|  
|--------|--------|-----------------|  
|\<|`<`|より小さい記号|  
|\>|`>`|より大きい記号|  
|&|`&`|アンパサンド記号|  
|"|`"`|二重引用符記号|  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] メモ帳などのテキスト エディターを使用してマークアップ ファイルを作成する場合は、エンコードされた特殊文字を保持するためにファイルを [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF\-8 ファイル形式で保存する必要があります。  
  
 マークアップを作成するときにテキストで特殊文字を使用する方法を次の例に示します。  
  
## 使用例  
 [!code-xml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]