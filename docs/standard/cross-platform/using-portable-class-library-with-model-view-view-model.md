---
title: "Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "汎用性のあるクラス ライブラリ [.NET Framework]、および MVVM"
  - "MVVM、および汎用性のあるクラス ライブラリ"
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Model-View-View Model を利用した汎用性のあるクラス ライブラリの使用
Model\-View\-View Model \(MVVM\) パターンを実装し、複数のプラットフォーム間でアセンブリを共有するには、.NET Framework [ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) を使用できます。  
  
 MVVM は、基になるビジネス ロジックからのユーザー インターフェイスを分離するアプリケーション パターンです。  [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]の [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] のプロジェクトのモデルおよびビュー モデル クラスを実装し、異なるプラットフォーム用にカスタマイズされたビューを作成します。  この方法は一度だけデータ モデルおよびビジネス ロジックを記述できるようになり、次の図に示すように、.NET Framework、Silverlight、Windows Phone、および [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] のアプリケーションからのコードを使用します。  
  
 ![MVVM を使用したポータブルのダイアグラム](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 このトピックには MVVM パターンに関する一般的な情報は含まれていません。  [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] を使用して MVVM を実装する方法についてのみ説明します。  MVVM の詳細については、MSDN [MVVM Quickstart](http://go.microsoft.com/fwlink/?LinkId=234934) ライブラリを参照します。  
  
## MVVM をサポートしているクラス  
 [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] プロジェクトに対し、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]、Silverlight、または Windows Phone 7.5 を対象とする場合は、MVVM パターンの実装に次のクラスを使用できます。  
  
-   <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName> クラス  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=fullName> クラス  
  
-   <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=fullName> クラス  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=fullName> クラス  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=fullName> クラス  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=fullName> クラス  
  
-   <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=fullName> クラス  
  
-   <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=fullName> クラス  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=fullName> クラス  
  
-   <xref:System.Windows.Input.ICommand?displayProperty=fullName> クラス  
  
-   <xref:System.ComponentModel.DataAnnotations?displayProperty=fullName> 名前空間のすべてのクラス  
  
## MVVM の実装  
 MVVM を実装するには、通常はモデルとビュー モデルの両方を [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] プロジェクト内に作成します。[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] プロジェクトは非移植性のプロジェクトを参照できないためです。  モデルおよびビュー モデルは、同じプロジェクトに含めることも、個別のプロジェクトに含めることもできます。  異なるプロジェクトを使用する場合は、ビュー モデル プロジェクトからの参照をモデル プロジェクトに追加します。  
  
 モデルおよびビュー モデルのプロジェクトをコンパイルした後は、ビューを含むアプリケーションでこれらのアセンブリを参照します。  ビューがビュー モデルのみと対話する場合は、ビュー モデルを含むアセンブリを参照するだけで済みます。  
  
### モデル  
 次の例は、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] プロジェクトに含めることのできる簡易モデル クラスを示しています。  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 以下に、[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] プロジェクトでのデータの挿入、取得、および更新の簡単な方法例を示します。  実際のアプリケーションでは、データは Windows Communication Foundation \(WCF\) サービスなどのソースから取得します。  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### ビュー モデル  
 ビュー モデルの基本クラスは MVVM パターンの実装時に追加されることがよくあります。  基本クラスの例を次に示します。  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 MVVM パターンでは <xref:System.Windows.Input.ICommand> インターフェイスの実装がよく使用されます。  <xref:System.Windows.Input.ICommand> インターフェイスを実装する例を次に示します。  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 簡易ビュー モデルの例を次に示します。  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### ビュー  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] アプリケーション、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーション、Silverlight ベースのアプリケーション、または Windows Phone 7.5 アプリケーションでは、モデルおよびビュー モデルのプロジェクトを含むアセンブリを参照できます。次に、ビュー モデルと対話するビューを作成します。  次の例では、ビュー モデルからデータを取得し、更新する簡易 Windows Presentation Foundation \(WPF\) アプリケーションを示します。  似たようなビューは Silverlight、Windows Phone、または [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーションでも作成できます。  
  
 [!code-xml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## 参照  
 [汎用性のあるクラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)