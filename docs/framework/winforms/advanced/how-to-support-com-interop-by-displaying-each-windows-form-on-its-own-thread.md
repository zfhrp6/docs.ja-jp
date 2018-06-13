---
title: '方法 : 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートする'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: c78bcc8d784fc481af2449f2d81cfde42891e7fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522890"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>方法 : 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートする
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] メッセージ ループでフォームを表示して、COM 相互運用性の問題を解決できます。これは、<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> メソッドを使用して作成することができます。  
  
 Windows フォームが COM クライアント アプリケーションから正しく動作するには、Windows フォームのメッセージ ループ上でフォームを実行する必要があります。 そのためには、次の方法のいずれかを使用します。  
  
-   <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用して、Windows フォームを表示します。 詳細については、「 [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)」を参照してください。  
  
-   各 Windows フォームを別のスレッドで表示します。  
  
 Visual Studio では、この機能の広範なサポートがあります。  
  
 「 [チュートリアル: Windows フォームを別個のスレッドに表示することによって COM 相互運用をサポートする](http://msdn.microsoft.com/library/ms233639\(v=vs.110\))」も参照してください。  
  
## <a name="example"></a>例  
 次のコード例は、個別のスレッドでフォームを表示し、<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> メソッドを呼び出して、スレッドで Windows フォーム メッセージ ポンプを開始する方法を示しています。 この方法を使用するには、 <xref:System.Windows.Forms.Control.Invoke%2A> メソッドを使用して、アンマネージ アプリケーションからのフォームの呼び出しをマーシャリングする必要があります。  
  
 この方法は、独自のメッセージ ループを使用して、独自のスレッドで、フォームの各インスタンスが実行する必要があります。 1 つのスレッドに対して複数のメッセージ ループを実行することはできません。 そのため、クライアント アプリケーションのメッセージ ループを変更することはできません。 ただし、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] コンポーネントを変更して、独自のメッセージ ループを使用する新しいスレッドを開始することができます。  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   `COMForm`、 `Form1`、および `FormManager` の型を、 `COMWinform.dll`と呼ばれるアセンブリにコンパイルします。 「 [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)」で説明するメソッドのいずれかを使用して COM にアセンブリを登録します。 これで、アンマネージ アプリケーションのアセンブリと対応する型のライブラリ (.tlb) ファイルを使用できます。 たとえば、Visual Basic 6.0 の実行可能なプロジェクトで参照として型ライブラリを使用することができます。  
  
## <a name="see-also"></a>関連項目  
 [COM への .NET Framework コンポーネントの公開](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [COM 用のアセンブリのパッケージ化](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [COM へのアセンブリの登録](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [方法: ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Windows フォームおよびアンマネージ アプリケーションの概要](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
