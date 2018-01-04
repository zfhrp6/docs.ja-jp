---
title: "方法 : BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3983b2544a4586f6f53e19a7f5fcdcd384a6bc2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>方法 : BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる
データ ソースに含まれる型が <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装し、プロパティ値が変更されると <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> イベントを発生させる場合に、<xref:System.Windows.Forms.BindingSource> コンポーネントがデータ ソースの変更を自動的に検出します。 これは、データ ソースの値が変わると、<xref:System.Windows.Forms.BindingSource> にバインドされるコントロールが自動的に更新されるため便利です。  
  
> [!NOTE]
>  データ ソースが <xref:System.ComponentModel.INotifyPropertyChanged> を実装し、非同期操作を実行している場合は、バック グラウンド スレッド上のデータ ソースを変更しないようにします。 代わりに、バック グラウンド スレッド上のデータを読み取り、UI スレッドでリストにデータをマージする必要があります。  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスの簡単な実装を示します。 <xref:System.Windows.Forms.BindingSource> が <xref:System.ComponentModel.INotifyPropertyChanged> 型の一覧にバインドされるときに、<xref:System.Windows.Forms.BindingSource> がバインドされたコントロールにデータ ソースの変更を自動的に渡す方法も示します。  
  
 `CallerMemberName` 属性を使用する場合、`NotifyPropertyChanged` メソッドの呼び出しが、文字列引数としてプロパティ名を指定する必要はありません。 詳細については、次を参照してください。[呼び出し元情報](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373)です。  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  参照してください["http://msdn.microsoft.com/library/bb129228(v=vs.110)"のハイパーリンクをする方法: コンパイルし、完成した Windows フォーム コードの例を使用して Visual Studio を実行](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))です。  
  
## <a name="see-also"></a>参照  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [方法: BindingSource ResetItem メソッドを使用して変更通知を発生させる](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
