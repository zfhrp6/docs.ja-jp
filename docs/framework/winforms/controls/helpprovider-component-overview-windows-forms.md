---
title: HelpProvider コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: 5ad74b862c09734f3490210cb6898945a3c787fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528620"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider コンポーネントの概要 (Windows フォーム)
Windows フォーム[HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)に HTML ヘルプ 1.x のヘルプ ファイル (HTML Help Workshop で生成された .chm ファイル、または .htm ファイル) を Windows アプリケーションに関連付けるコンポーネントを使用します。 さまざまな方法でヘルプを提供することができます。  
  
-   Windows フォーム上のコントロールには、状況依存のヘルプを提供します。  
  
-   特定のダイアログ ボックスまたはダイアログ ボックスの特定のコントロールでは、状況依存のヘルプを提供します。  
  
-   テーブルの内容、インデックス、または検索機能のメイン ページなどの特定領域へのヘルプ ファイルを開きます。  
  
## <a name="using-the-help-provider"></a>ヘルプのプロバイダーを使用します。  
 追加する、<xref:System.Windows.Forms.HelpProvider>コンポーネントを Windows フォームのヘルプ プロパティを公開するフォーム上の他のコントロールを使用して、<xref:System.Windows.Forms.HelpProvider>コンポーネントです。 これにより、Windows フォーム上のコントロールのヘルプを提供することができます。 ヘルプ ファイルを関連付けることができます、<xref:System.Windows.Forms.HelpProvider>コンポーネントを使用して、<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>プロパティです。 呼び出しによって提供されるヘルプの種類を指定する<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>から値を指定する、<xref:System.Windows.Forms.HelpNavigator>指定したコントロールの列挙。 呼び出してヘルプのキーワードまたはトピックを提供する、<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>メソッドです。  
  
 必要に応じて、特定のヘルプ文字列を別のコントロールに関連付けるを使用して、<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>メソッドです。 このメソッドを使用して、コントロールに関連付ける文字列は、コントロールにフォーカスがある状態で F1 キーを押したときに、ポップアップ ウィンドウに表示されます。  
  
 場合<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>設定された場合、使用する必要がありますされていません。<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>ヘルプ テキストを提供します。 両方を設定した場合<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>ヘルプ文字列ヘルプに基づいて<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>が優先されます。  
  
> [!NOTE]
>  相対パスを使用して問題が発生する可能性があるときにヘルプ ファイルへのパスを指定するで、<xref:System.Windows.Forms.Help.ShowHelp%2A>メソッドまたは<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>のプロパティ、<xref:System.Windows.Forms.HelpProvider>コントロール。 そのため、ヘルプ ファイルを指定するファイルの絶対パスを使用することを確認します。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム アプリケーションのヘルプ システム](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
