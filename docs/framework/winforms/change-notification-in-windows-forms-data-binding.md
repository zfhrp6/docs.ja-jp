---
title: Windows フォーム データ バインディングの変更通知
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 79ad52b6db8cb7be7f4e3162b8f726e8cbe22dcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Windows フォーム データ バインディングの変更通知
Windows フォーム データ バインディングの最も重要な概念の 1 つは*変更通知*です。 データ ソースとバインドされたコントロール常に最新のデータを入手するには、データ バインディングの変更通知を追加する必要があります。 具体的には、バインドされたコントロールが、データ ソースに加えられた変更の通知を受け取ることを保証して、データ ソースは、コントロールのバインド プロパティに対して行われた変更の通知です。  
  
 データ バインディングの種類に応じて、変更通知のさまざまな種類があります。  
  
-   1 つのコントロール プロパティがオブジェクトの 1 つのインスタンスにバインドされている単純なバインディング。  
  
-   一覧内の項目のプロパティまたはコントロールのプロパティにバインドされている 1 つのコントロール プロパティを含めることができますが、リストベース バインディングは、オブジェクトの一覧にバインドされます。  
  
 また場合に、データ バインディングに使用する Windows フォーム コントロールを作成するには、適用、 *PropertyName*にコントロールのバインドのプロパティに対する変更を反映するように、コントロールにパターンを変更しますデータ ソースです。  
  
## <a name="change-notification-for-simple-binding"></a>単純なバインディングの変更通知  
 単純バインディングは、バインドされたプロパティの値が変更されたときに、ビジネス オブジェクトは変更通知を提供する必要があります。 公開することでこれを行う、 *PropertyName*Changed イベントを持つコントロールへのビジネス オブジェクトのバインド、ビジネス オブジェクトの各プロパティについて、<xref:System.Windows.Forms.BindingSource>またはビジネス オブジェクトを実装する推奨される方法<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスとが発生し、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベント プロパティの値が変更されたときにします。 詳細については、次を参照してください。[する方法: INotifyPropertyChanged インターフェイスを実装して](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)です。 実装するオブジェクトを使用すると、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスがありませんを使用する、 <xref:System.Windows.Forms.BindingSource> 、オブジェクトをコントロールにバインドするを使用して、<xref:System.Windows.Forms.BindingSource>をお勧めします。  
  
## <a name="change-notification-for-list-based-binding"></a>リストに基づくバインディングの変更通知  
 Windows フォームは、プロパティの変更 (リスト項目プロパティの値を変更) を提供するバインドされたリストとリストの変更によって異なります。 (アイテムが削除または一覧に追加) 情報をコントロールをバインドします。 したがって、データ バインディングを使用するリストを実装する必要があります、 <xref:System.ComponentModel.IBindingList>、両方の種類の変更通知を提供します。 <xref:System.ComponentModel.BindingList%601> 、ジェネリック型の実装は、<xref:System.ComponentModel.IBindingList>し、Windows フォーム データ バインディングを使用するために設計されています。 作成することができます、<xref:System.ComponentModel.BindingList%601>を実装するビジネス オブジェクトの種類を格納している<xref:System.ComponentModel.INotifyPropertyChanged>一覧は自動的に変換し、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベント<xref:System.ComponentModel.IBindingList.ListChanged>イベント。 バインドされたリストがない場合、<xref:System.ComponentModel.IBindingList>を使用して、オブジェクトの一覧を Windows フォーム コントロールにバインドする必要があります、<xref:System.Windows.Forms.BindingSource>コンポーネントです。 <xref:System.Windows.Forms.BindingSource>コンポーネントと類似のプロパティのリストへの変換を提供、<xref:System.ComponentModel.BindingList%601>です。 詳細については、次を参照してください。[する方法: BindingSource と INotifyPropertyChanged インターフェイスを使用して変更通知を発生させる](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)です。  
  
## <a name="change-notification-for-custom-controls"></a>カスタム コントロールの変更通知  
 最後に、制御側の必要がありますを公開する、 *PropertyName*データにバインドするように設計の各プロパティの変更イベント。 コントロール プロパティへの変更は、バインド データ ソースに反映し、されます。 詳細については、次を参照してください[する方法: PropertyNameChanged パターンを適用。](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Windows フォームでのデータ バインディング](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Windows フォームがサポートするデータ ソース](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
