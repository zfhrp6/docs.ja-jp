---
title: "Windows フォーム データ バインドの変更通知 | Microsoft Docs"
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
  - "Windows フォーム, 追加 (データ バインディングの変更通知を)"
  - "Windows フォーム, データ バインド"
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Windows フォーム データ バインドの変更通知
Windows フォーム データ バインディングの重要な概念の 1 つに、"変更通知" があります。  データ ソースとデータ バインド コントロールに常に最新のデータを持たせるためには、データ バインディングの変更通知を追加する必要があります。  具体的には、データ ソースに加えられた変更がバインド コントロールに通知され、コントロールのバインド プロパティに加えられた変更がデータ ソースに通知されるようにします。  
  
 次のように、データ バインディングの種類に応じて異なる種類の変更通知があります。  
  
-   単純バインディング。1 つのコントロール プロパティがオブジェクトの 1 つのインスタンスにバインドされます。  
  
-   リストベース バインディング。リスト内のアイテムのプロパティにバインドされる 1 つのコントロール プロパティ、またはオブジェクトのリストにバインドされるコントロール プロパティを含むことができます。  
  
 さらに、データ バインディングで使用する Windows フォーム コントロールを作成する場合、コントロールのバインド プロパティに対する変更がデータ ソースに反映されるように、コントロールに *PropertyName*Changed パターンを適用する必要があります。  
  
## 単純バインディングの変更通知  
 単純バインディングでは、バインド プロパティの値が変更されたときにビジネス オブジェクトが変更通知を出す必要があります。  これは、ビジネス オブジェクトの各プロパティに対して *PropertyName*Changed イベントを公開し、<xref:System.Windows.Forms.BindingSource> またはビジネス オブジェクトが <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装してプロパティの値が変更されたときに <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> イベントを起動するメソッドを使用して、ビジネス オブジェクトをコントロールにバインドすることによって実現できます。  詳細については、「[方法 : INotifyPropertyChanged インターフェイスを実装する](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)」を参照してください。  <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装するオブジェクトを使用する場合、オブジェクトをコントロールにバインドするために <xref:System.Windows.Forms.BindingSource> を使用する必要はありませんが、<xref:System.Windows.Forms.BindingSource> の使用を推奨します。  
  
## リストベース バインディングの変更通知  
 Windows フォームは、バインド リストに依存して、プロパティ変更 \(リスト アイテム プロパティ値の変更\) および変更されたリスト \(リストに対するアイテムの削除や追加\) の情報をバインド コントロールに提供します。  このため、データ バインディングに使用するリストには、両方の種類の変更通知を提供する <xref:System.ComponentModel.IBindingList> を実装する必要があります。  <xref:System.ComponentModel.BindingList%601> は、<xref:System.ComponentModel.IBindingList> の汎用実装で、Windows フォーム データ バインディングで使用するためにデザインされています。  <xref:System.ComponentModel.INotifyPropertyChanged> を実装するビジネス オブジェクト タイプを含む <xref:System.ComponentModel.BindingList%601> を作成できます。リストは <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> イベントを <xref:System.ComponentModel.IBindingList.ListChanged> イベントに自動的に変換します。  バインド リストが <xref:System.ComponentModel.IBindingList> でない場合、オブジェクトのリストを <xref:System.Windows.Forms.BindingSource> コンポーネントを使用して Windows フォーム コントロールにバインドする必要があります。  <xref:System.Windows.Forms.BindingSource> コンポーネントは、<xref:System.ComponentModel.BindingList%601> の場合と同様にプロパティからリストへの変換を行います。  詳細については、「[方法 : BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)」を参照してください。  
  
## カスタム コントロールの変更通知  
 最後に、コントロール側から、データにバインドされるようにデザインされた各プロパティに *PropertyName*Changed イベントを公開する必要があります。  これで、コントロール プロパティに対する変更は、バインド データ ソースに反映されます。  詳細については、「[方法 : PropertyNameChanged パターンを適用する](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.ComponentModel.INotifyPropertyChanged>   
 <xref:System.ComponentModel.BindingList%601>   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Windows フォームがサポートするデータ ソース](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)   
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)