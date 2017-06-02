---
title: "ErrorProvider コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ErrorProvider"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "エラー メッセージ, 表示"
  - "ErrorProvider コンポーネント [Windows フォーム], ErrorProvider コンポーネントの概要"
  - "エラー [Windows フォーム], 表示 (ユーザーに)"
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ErrorProvider コンポーネントの概要 (Windows フォーム)
Windows フォームの [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) コンポーネントは、フォームまたはコントロールへのユーザー入力を検証するために使用します。  通常は、ユーザーがフォームに入力した値の妥当性を検査するとき、またはデータセット内のエラーを表示するときに使用します。  メッセージ ボックスにエラー メッセージを表示する方法もありますが、メッセージ ボックスを閉じるとエラー メッセージを見ることができなくなるため、エラー プロバイダーを使用する方が確実です。  <xref:System.Windows.Forms.ErrorProvider> コンポーネントは、テキスト ボックスなどの該当するコントロールの隣にエラー アイコン \(![ErrorProvider アイコン](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.png "vbErrorProviderIcon")\) を表示します。エラー アイコンの上にマウス ポインターを置くと、エラー メッセージの文字列を表示するツールヒントが表示されます。  
  
## 主要なプロパティ  
 <xref:System.Windows.Forms.ErrorProvider> コンポーネントの主要なプロパティは、<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>、および <xref:System.Windows.Forms.ErrorProvider.Icon%2A> です。  <xref:System.Windows.Forms.ErrorProvider> コンポーネントを、データがバインドされているコントロールと組み合わせて使用している場合、コンポーネントでフォーム上にエラー アイコンを表示するには、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> プロパティに適切なコンテナー \(通常は Windows フォーム\) を設定する必要があります。  デザイナーでこのコンポーネントを追加すると、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> プロパティには、コンポーネントを包含しているフォームが設定されます。コンポーネントをコードで追加する場合は、開発者が設定する必要があります。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> プロパティには、既定のアイコンに代えて独自のエラー アイコンを設定できます。  <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> プロパティを設定すると、<xref:System.Windows.Forms.ErrorProvider> コンポーネントで特定のデータセットに関するエラー メッセージを表示できます。  <xref:System.Windows.Forms.ErrorProvider> コンポーネントの主要なメソッドは、<xref:System.Windows.Forms.ErrorProvider.SetError%2A> メソッドです。このメソッドを使用して、エラー メッセージの文字列と、エラー アイコンの表示位置を指定します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> コンポーネントには、ユーザー補助クライアントの組み込みサポート機能は準備されていません。  このコンポーネントを使用する場合に、アプリケーションをユーザー補助対応にするには、新たにユーザー補助フィードバック機構を提供する必要があります。  
  
## 参照  
 <xref:System.Windows.Forms.ErrorProvider>   
 [方法 : Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)   
 [方法 : Windows フォーム ErrorProvider コンポーネントを使用してフォーム妥当性検査でエラー アイコンを表示する](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)