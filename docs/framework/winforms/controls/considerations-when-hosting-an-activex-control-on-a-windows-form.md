---
title: Windows フォームで ActiveX コントロールをホストする場合の考慮事項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 52977ea11745056f7e022d545705d989d2e1bbc8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526238"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Windows フォームで ActiveX コントロールをホストする場合の考慮事項
Windows フォームは、Windows フォーム コントロールをホストするために最適化されていますが、ActiveX コントロールを使うこともできます。 ActiveX コントロールを使うアプリケーションを計画するときは、次の考慮事項に留意してください。  
  
-   **セキュリティ** 共通言語ランタイムは、コード アクセス セキュリティに関して強化されました。 Windows フォームを使うアプリケーションは、完全に信頼された環境では問題なく動作し、信頼性が高くない環境ではほとんどの機能がアクセス可能な状態で動作します。 Windows フォーム コントロールは、ブラウザーで問題なくホストできます。 ただし、Windows フォームの ActiveX コントロールは、これらのセキュリティ強化を利用できません。 ActiveX コントロールの実行で設定されているアンマネージ コードのアクセス許可が必要です、<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType>プロパティです。 セキュリティとアンマネージ コードのアクセス許可の詳細については、次を参照してください。<xref:System.Security.Permissions.SecurityPermissionAttribute>です。  
  
-   **総保有コスト** Windows フォームに追加される ActiveX コントロールは、その Windows フォーム全体と共に配置されるため、作成されるファイルのサイズが大幅に追加する可能性があります。 さらに、Windows フォームで ActiveX コントロールを使うには、レジストリへの書き込みが必要です。 これは、レジストリへの書き込みを必要としない Windows フォーム コントロールと比較して、ユーザーのコンピューターに大きく干渉します。  
  
    > [!NOTE]
    >  ActiveX コントロールを操作するには、COM 相互運用ラッパーを使う必要があります。 詳しくは、「[Visual Basic および Visual C# における COM 相互運用性](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)」をご覧ください。  
  
    > [!NOTE]
    >  ActiveX コントロールのメンバーの名前で定義された名前に一致する場合、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]、ActiveX コントロール インポーターでメンバー名のプレフィックスは、 **Ctl**を作成すると、<xref:System.Windows.Forms.AxHost>クラスを派生します。 たとえば、ActiveX コントロールに **Layout** という名前のメンバーがある場合、**Layout** イベントが [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 内で定義されているため、AxHost 派生クラスでは **CtlLayout** という名前に変更されます。  
  
## <a name="see-also"></a>関連項目  
 [方法: Windows フォームに ActiveX コントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [コード アクセス セキュリティ](../../../../docs/framework/misc/code-access-security.md)  
 [各言語およびライブラリにおける、コントロールとプログラミング可能オブジェクトの比較](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Windows フォームへのコントロールの追加](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)
