---
title: "XML Character Entities and XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "&"
  - "&amp"
  - "&gt"
  - "&lt"
helpviewer_keywords: 
  - "XAML [XAML Services], special characters"
  - "ampersand (&) [XAML Services]"
  - "special characters [XAML Services]"
  - "apostrophe (') [XAML Services]"
  - "greater-than (>) character [XAML Services]"
  - "XAML [XAML Services], quotation mark (")"
  - "XAML [XAML Services], apostrophe (')"
  - "& (ampersand) [XAML Services]"
  - "XAML [XAML Services], & (ampersand)"
  - "XAML [XAML Services], escape sequence"
  - "quotation mark (") [XAML Services]"
  - "less-than (<) character [XAML Services]"
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: 23
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 21
---
# XML Character Entities and XAML
XAML は、特殊文字に、XML で定義される文字エンティティを使用します。  ここでは、いくつかの特定の文字エンティティ、および XAML における他の XML の概念に関する一般的な考慮事項について説明します。  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## XAML に固有の文字のエンティティとエスケープの問題  
 XAML マークアップでは、一般に、XML で定義されているものと同じ文字エンティティおよびエスケープ シーケンスを使用します。  
  
 大きな違いは、XAML では中かっこ \({ と }\) が意味を持つ点です。中かっこで囲まれた文字シーケンスは、マークアップ拡張機能として解釈する必要があることを XAML プロセッサに通知します。  マークアップ拡張機能の詳細については、「[Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)」を参照してください。  
  
 ただし、XML ではなく XAML に固有のエスケープ シーケンスを使用すると、中かっこをリテラル文字として表示できます。  詳細については、「[{} Escape Sequence \/ Markup Extension](../../../docs/framework/xaml-services/escape-sequence-markup-extension.md)」を参照してください。  
  
 円記号 \(\\\) は、文字列として処理する場合、エスケープ シーケンスは必要ありません。  
  
<a name="xml_character_entities"></a>   
## XML 文字エンティティ  
 前に述べたように、XAML マークアップを記述するときに一般的に使用する文字エンティティおよびエスケープ シーケンスの大半は、XML で定義されています。  このトピックでは、こうしたエンティティの一覧は示しません。エンティティの詳細なリファレンスについては、XML 仕様などの外部ドキュメントを参照してください。  ただし、このトピックでは、便宜を考えて、XAML マークアップでよく使用する XML 文字エンティティを抜粋した一覧を示します。  
  
|文字|Entity|ノート|  
|--------|------------|---------|  
|& \(アンパサンド\)|&amp;|属性値および要素の内容の両方に対して使用する必要があります。|  
|\> \(大なり記号\)|&gt;|属性値に対しては使用する必要があります。要素の内容に対しては、前に \< がない限りは、\> を使用できます。|  
|\< \(小なり記号\)|&lt;|属性値に対しては使用する必要があります。要素の内容に対しては、後に \> がない限りは、\< を使用できます。|  
|" \(二重引用符\)|&quot;|属性値に対しては使用する必要があります。要素の内容としては、二重引用符 \("\) も受け入れられます、  属性値は、単一引用符 \('\) と二重引用符 \("\) のどちらかで囲むことができます。最初に使用したほうの引用符が、属性値を囲む文字になり、もう一方の引用符は値の中でリテラルとして使用できます。|  
|' \(単一引用符\)|&apos;|属性値に対しては使用する必要があります。要素の内容としては、単一引用符 \('\) も受け入れられます、  属性値は、単一引用符 \('\) と二重引用符 \("\) のどちらかで囲むことができます。最初に使用したほうの引用符が、属性値を囲む文字になり、もう一方の引用符は値の中でリテラルとして使用できます。|  
|\(数値と文字の対応付け\)|&\#*\[整数\]*; または &\#x*\[16 進数\]*;|XAML では、アクティブなエンコーディングに応じた数値と文字の対応付けがサポートされています。|  
|\(改行しないスペース\)|&\#160; \(UTF\-8 エンコーディングを想定\)|フロー ドキュメントの要素、または WPF の <xref:System.Windows.Controls.TextBox> などのテキストを受け取る要素では、マークアップからの改行しないスペースの正規化は行われません。これには、`xml:space="default"` の場合も含まれます。  詳細については、「[Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)」を参照してください\)。|  
  
<a name="xml_comment_format"></a>   
## XML のコメントの書式  
 XAML では、XML のコメントの書式を使用します。つまり、コメントの先頭は `<!--` で表し、コメントの末尾は `-->,` で表します。コメントの中に `--` というシーケンスを含めることはできません。  
  
<a name="xml_processing_instructions"></a>   
## XML 処理命令  
 XAML では、XML 仕様に従って XML 処理命令が処理されます。つまり、命令は必ず素通しされます。  .NET Framework XAML サービスの XAML 処理では、処理命令は使用されません。  XAML を使用する他の既存のフレームワークでも、XAML の処理命令は使用されません。  
  
## 参照  
 [{} Escape Sequence \/ Markup Extension](../../../docs/framework/xaml-services/escape-sequence-markup-extension.md)   
 [XAML の概要 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../ocs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [XamlName の文法](../../../docs/framework/xaml-services/xamlname-grammar.md)   
 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)