---
title: "Windows フォームでのデータ バインド | Microsoft Docs"
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
  - "バインド コントロール, Windows フォーム"
  - "データ [Windows フォーム]"
  - "データ [Windows フォーム], アーキテクチャ"
  - "Windows フォーム コントロール, データ バインディング"
  - "Windows フォーム, データ バインディング"
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Windows フォームでのデータ バインド
Windows フォームでのデータ バインドは、データ ソースの情報をフォーム上のコントロールで表示したり変更したりする手段を提供します。  従来のデータ ソースに対してだけでなく、データを格納したほとんどすべての構造に対してバインドできます。  
  
## このセクションの内容  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 Windows フォームのデータ バインドの概要を説明します。  
  
 [Windows フォームがサポートするデータ ソース](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 Windows フォームで使用できるデータ ソースについて説明します。  
  
 [データ連結に関連するインターフェイス](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 Windows フォームのデータ バインドで使用されるいくつかのインターフェイスについて説明します。  
  
 [方法 : Windows フォームでデータ間を移動する](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 データ ソースの項目間を移動する方法を示します。  
  
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 Windows フォーム データ バインドの異なる種類の変更通知について説明します。  
  
 [方法 : INotifyPropertyChanged インターフェイスを実装する](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装する方法について説明します。  インターフェイスは、バインドしたコントロールを通してビジネス オブジェクトのプロパティの変更内容を通信します。  
  
 [方法 : PropertyNameChanged パターンを適用する](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 Windows フォームのユーザー コントロールのプロパティに *PropertyName*Changed パターンを適用する方法について説明します。  
  
 [方法 : ITypedList インターフェイスを実装する](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <xref:System.ComponentModel.ITypedList> インターフェイスを実装して、バインドできるリストのスキーマを検出できるようにする方法について説明します。  
  
 [方法 : IListSource インターフェイスを実装する](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <xref:System.ComponentModel.IListSource> インターフェイスを実装して、<xref:System.Collections.IList> を実装する代わりに別の場所からリストを提供する、バインドできるクラスを作成する方法について説明します。  
  
 [方法 : 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <xref:System.Windows.Forms.BindingSource.BindingComplete> イベントを処理して、データ ソースにバインドされているすべてのコントロールの同期を保つ方法について説明します。  
  
 [方法 : 子テーブルの選択行が現在位置を保持することを保証する](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 親テーブルのフィールドが変更された場合に、子テーブルの選択行が変更されないことを保証する方法について説明しています。  
  
 「[データ バインディングに関連するインターフェイス](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\))」、「[方法 : Windows フォームでデータ間を移動する](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\))」、「[方法 : Windows フォームに単純バインド コントロールを作成する](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\))」も参照してください。  
  
## 関連項目  
 <xref:System.Windows.Forms.Binding?displayProperty=fullName>  
 バインドできるコンポーネントとデータ ソースの間のバインディングを表すクラスについて説明します。  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=fullName>  
 コントロールにバインドするためにデータ ソースをカプセル化するクラスについて説明します。  
  
## 関連項目  
 [BindingSource コンポーネント](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <xref:System.Windows.Forms.BindingSource> コンポーネントの使用方法の例を示すトピックの一覧を示します。  
  
 [DataGridView コントロール](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 バインドできるデータ グリッド コントロールの使用方法の例を示すトピックの一覧を示します。  
  
 「[Visual Studio でのデータへのアクセス](http://msdn.microsoft.com/library/wzabh8c4\(v=vs.110\))」または「[Visual Studio でのデータへのアクセス](http://msdn.microsoft.com/library/wzabh8c4\(v=vs.110\))」も参照してください。