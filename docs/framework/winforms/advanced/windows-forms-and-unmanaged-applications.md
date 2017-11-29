---
title: "Windows フォームとアンマネージ アプリケーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8166ab6a69ce9a774e83e6dbc7278a41805f7a83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows フォームとアンマネージ アプリケーション
Windows フォーム アプリケーションとコントロールは、いくつかの注意事項がありますが、アンマネージ アプリケーションと相互運用できます。 次のセクションでは、Windows フォーム アプリケーションとコントロールがサポートするシナリオと構成、および、サポートしないシナリオと構成について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows フォームおよびアンマネージ アプリケーションの概要](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 アンマネージ アプリケーションで使用する Windows フォーム コントロールを実装する方法に関する一般的な情報を提供します。  
  
 [方法: ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用して Windows フォームをアンマネージ アプリケーションで実行する方法を示すコード例を提供します。  
  
 [方法: 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートする](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 独自のスレッドで Windows フォームを実行する方法を示すコード例を提供します。  
  
 「 [チュートリアル: Windows フォームを別個のスレッドに表示することによって COM 相互運用をサポートする](http://msdn.microsoft.com/library/ms233639\(v=vs.110\))」も参照してください。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Windows フォーム用の個別のスレッドの作成に使用します。  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 スレッドのメッセージ ループを開始します。  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 フォームにアンマネージ アプリケーションからの呼び出しをマーシャリングします。  
  
## <a name="related-sections"></a>関連項目  
 [COM への .NET Framework コンポーネントの公開](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 .NET Framework の型をアンマネージ アプリケーションで使用する方法に関する一般情報を提供します。
