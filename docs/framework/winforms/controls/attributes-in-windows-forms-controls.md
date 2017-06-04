---
title: "Windows フォーム コントロールの属性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "属性 [Windows フォーム]"
  - "属性 [Windows フォーム], クラス"
  - "属性 [Windows フォーム], コントロールのプロパティ"
  - "属性 [Windows フォーム], データ バインディング プロパティ"
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows フォーム コントロールの属性
.NET Framework には、カスタム コントロールとカスタム コンポーネントのメンバーに適用できるさまざまな属性が用意されています。  これらの属性には、クラスの実行時の動作に影響するものと、デザイン時の動作に影響するものがあります。  
  
## コントロールとコンポーネントのプロパティの属性  
 カスタム コントロールとカスタム コンポーネントのプロパティやその他のメンバーに適用できる属性を次の表に示します。  これらの属性の使用例については、「[方法 : Windows フォーム コントロールに属性を適用する](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)」を参照してください。  
  
|属性|Description|  
|--------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|プロパティが別のソースからその値を取得できるようにするために、プロパティに渡す値を指定します。  これは、*アンビエンス*と呼ばれます。|  
|<xref:System.ComponentModel.BrowsableAttribute>|プロパティまたはイベントを **\[プロパティ\]** ウィンドウに表示するかどうかを指定します。|  
|<xref:System.ComponentModel.CategoryAttribute>|<xref:System.Windows.Forms.PropertySort> モードに設定された <xref:System.Windows.Forms.PropertyGrid> コントロールにプロパティまたはイベントを表示するときに、それらをグループ化するためのカテゴリの名前を指定します。|  
|<xref:System.ComponentModel.DefaultValueAttribute>|プロパティの既定値を指定します。|  
|<xref:System.ComponentModel.DescriptionAttribute>|プロパティまたはイベントの説明を指定します。|  
|<xref:System.ComponentModel.DisplayNameAttribute>|プロパティ、イベント、または引数を受け取らない `public` `void` メソッドの表示名を指定します。|  
|<xref:System.ComponentModel.EditorAttribute>|プロパティの変更に使用するエディターを指定します。|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|プロパティまたはメソッドをエディターで表示できるように指定します。|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|クラスまたはメンバーのコンテキスト キーワードを指定します。|  
|<xref:System.ComponentModel.LocalizableAttribute>|プロパティをローカライズするかどうかを指定します。|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|オブジェクトのテキスト表現が、アスタリスク \(\*\) などの文字で隠されることを示します。|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|この属性がバインドされているプロパティをデザイン時に読み取り専用にするか、読み書き両用にするかを指定します。|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|関連付けられているプロパティ値が変更されたときにプロパティ グリッドを更新することを示します。|  
|<xref:System.ComponentModel.TypeConverterAttribute>|この属性がバインドされているオブジェクトのコンバーターとして使用する型を指定します。|  
  
## データ バインディング プロパティの属性  
 カスタム コントロールやカスタム コンポーネントがデータ バインディング機能とやり取りする方法を指定する際に適用できる属性を、次の表に示します。  
  
|属性|Description|  
|--------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|一般にプロパティをバインディングで使用するかどうかを指定します。|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|コンポーネントのデータ ソース プロパティとデータ メンバー プロパティを指定します。|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|コンポーネントの既定のバインディング プロパティを指定します。|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|コンポーネントのデータ ソース プロパティとデータ メンバー プロパティを指定します。|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|属性のリダイレクトを有効にします。|  
  
## クラスの属性  
 カスタム コントロールとカスタム コンポーネントのデザイン時の動作を指定する際に適用できる属性を、次の表に示します。  
  
|属性|Description|  
|--------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|コンポーネントの既定のイベントを指定します。|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|コンポーネントの既定のプロパティを指定します。|  
|<xref:System.ComponentModel.DesignerAttribute>|コンポーネントのデザイン時のサービスの実装に使用するクラスを指定します。|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|クラスのデザイナーが特定のカテゴリに属すように指定します。|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|ツールボックス項目の属性を表します。|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|ツールボックス項目に使用するフィルター文字列とフィルターの種類を指定します。|  
  
## 参照  
 <xref:System.Attribute>   
 [方法 : Windows フォーム コントロールに属性を適用する](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)