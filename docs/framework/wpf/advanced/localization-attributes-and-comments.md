---
title: "ローカリゼーション属性とコメント | Microsoft Docs"
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
  - "ローカリゼーション, 属性"
  - "ローカリゼーション, コメント"
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# ローカリゼーション属性とコメント
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ローカリゼーション コメントは、ローカライズの規則やヒントを示すために、開発者が [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ソース コード内に記述するプロパティです。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ローカリゼーション コメントには、ローカライズ属性と自由な書式のローカリゼーション コメントの 2 組の情報が含まれます。  localizability 属性は、どのリソースがローカライズ対象かを示すために、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ローカリゼーション API により使用されます。  自由な書式のコメントには、アプリケーション作成者が必要に応じて任意の情報を記述できます。  
  
   
  
<a name="Localizer_Comments_"></a>   
## ローカリゼーション コメント  
 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 内の特定の要素について、テキストの長さ、フォント ファミリ、フォント サイズなどの制約がある場合、マークアップ アプリケーション作成者は [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] コード内のコメントを使用して、この情報をローカライザーに伝えることができます。  ソース コードにコメントを追加するためのプロセスは、次のとおりです。  
  
1.  アプリケーション開発者が、[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ソース コードにローカリゼーション コメントを追加します。  
  
2.  ビルド プロセスの間に、アセンブリ内に自由な書式のローカリゼーション コメントを残すか、コメントの一部を取り除くか、またはすべてのコメントを取り除くかどうかを、.proj ファイル内に指定できます。  取り除かれたコメントは、別のファイル内に保存されます。  `LocalizationDirectivesToLocFile` タグを使用してオプションを指定します。以下にその例を示します。  
  
     `<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`  
  
3.  指定できる値は次のとおりです。  
  
    -   **None** \- コメントと属性の両方がアセンブリ内に残され、別ファイルは生成されません。  
  
    -   **CommentsOnly** \- アセンブリからコメントだけが削除され、別の LocFile 内に保存されます。  
  
    -   **All** \- コメントと属性の両方がアセンブリから削除され、別の LocFile 内に保存されます。  
  
4.  [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] からローカライズ可能リソースが抽出されるときに、[!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] ローカリゼーション API により、localizability 属性に応じた処理が実行されます。  
  
5.  自由な書式のコメントだけを格納したローカリゼーション コメント ファイルは、ローカリゼーション プロセスに後から組み込まれます。  
  
 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ファイルにローカリゼーション コメントを追加する方法を次の例に\_示します。  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 この例では、Localization.Attributes セクションにローカリゼーション属性が、Localization.Comments セクションに自由な書式のコメントが記述されています。  次の表は、各属性とコメント、およびその意味を示したものです。  
  
|ローカリゼーション属性|説明|  
|-----------------|--------|  
|$Content \(Unmodifiable Readable Text\)|TextBlock 要素の内容は変更不能 \(Unmodifiable\) です。  ローカライザーは、「Microsoft」という単語を変更することはできません。  内容はローカライザーによる読み取りが可能 \(Readable\) です。  内容のカテゴリはテキストです。|  
|FontFamily \(Unmodifiable Readable\)|TextBlock 要素のフォント ファミリ プロパティは変更不能ですが、ローカライザーによる読み取りは可能です。|  
  
|自由な書式のローカリゼーション コメント|説明|  
|--------------------------|--------|  
|$Content \(Trademark\)|TextBlock 要素の内容が商標であることを示します。|  
|FontSize \(Trademark font size\)|フォント サイズ プロパティが標準の商標サイズに従う必要があることを示します。|  
  
### ローカライズ属性  
 Localization.Attributes セクション内の情報は、ターゲットの値名および関連付けられた localizability 値のペアのリストで構成されます。  ターゲット名には、プロパティ名または $Content 名のいずれかを指定します。  プロパティ名を指定した場合は、ターゲット値はプロパティの値になります。  $Content を指定した場合は、ターゲット値は要素の内容になります。  
  
 属性には次の 3 種類があります。  
  
-   **Category**。  値をローカライザー ツールで変更できる必要があるかどうかを指定します。  <xref:System.Windows.LocalizabilityAttribute.Category%2A> を参照してください。  
  
-   **Readability**。  ローカライザー ツールが値を読み取る \(および表示する\) 必要があるかどうかを指定します。  <xref:System.Windows.LocalizabilityAttribute.Readability%2A> を参照してください。  
  
-   **Modifiability**。  ローカライザー ツールが値の変更を許可するかどうかを指定します。  <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A> を参照してください。  
  
 これらの属性は、スペースで区切って任意の順番で指定できます。  同じ属性を重複して指定した場合は、最後に記述した属性が優先されます。  たとえば、Localization.Attributes \= "Unmodifiable Modifiable" と指定すると、最後の値である Modifiable が設定されます。  
  
 変更可能性と読み取り可能性については、説明は不要でしょう。  カテゴリ属性は、ローカライザーがテキストを翻訳する際の参考となるように、定義済みのカテゴリを示します。  Text、Label、Title などのカテゴリは、ローカライザーがテキストの翻訳方法を判断するうえで役立ちます。  さらに、None、Inherit、Ignore、NeverLocalize などの特別なカテゴリもあります。  
  
 特別なカテゴリの意味を次の表に示します。  
  
|\[カテゴリ\]|説明|  
|--------------|--------|  
|なし|ターゲット値には、定義されたカテゴリがありません。|  
|Inherit|ターゲット値は、親からカテゴリを継承します。|  
|\[無視\]|ターゲット値は、ローカリゼーション プロセスで無視されます。  Ignore は現在の値だけに影響します。  子ノードへの影響はありません。|  
|NeverLocalize|現在の値は、ローカライズ不能です。  このカテゴリは要素の子にも継承されます。|  
  
<a name="Localization_Comments"></a>   
## ローカリゼーション コメント  
 Localization.Comments セクションには、ターゲット値に関する自由な書式の文字列が含まれます。  アプリケーション開発者は、アプリケーション テキストの翻訳に関するヒントをローカライザーに伝える追加情報をここに記述します。  コメントには "\(\)" で囲んだ任意の文字列を記述できます。  文字のエスケープには '\\' を使用します。  
  
## 参照  
 [WPF のグローバリゼーション](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)   
 [自動レイアウトを使用してボタンを作成する](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)   
 [自動レイアウト用のグリッドを使用する](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)   
 [アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)