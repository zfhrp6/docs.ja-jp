---
title: "My.Forms オブジェクト"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a>My.Forms オブジェクト
現在のプロジェクトで宣言されている各 Windows フォームのインスタンスにアクセスするためには、プロパティを提供します。  
  
## <a name="remarks"></a>コメント  
 `My.Forms`オブジェクトが現在のプロジェクト内の各フォームのインスタンスを提供します。 プロパティの名前は、プロパティにアクセスするフォームの名前と同じです。 プロジェクトにフォームを追加する方法の詳細については、次を参照してください。[する方法: Windows フォームをプロジェクトに追加](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)です。  
  
 によって提供されるフォームにアクセスすることができます、`My.Forms`修飾なし、フォームの名前を使用してオブジェクト。 プロパティ名がフォームの型名と同じであるため、これにより、既定のインスタンスがあった場合、フォームにアクセスできます。 たとえば、`My.Forms.Form1.Show` は、`Form1.Show` と同じです。  
  
 `My.Forms`オブジェクトは、現在のプロジェクトに関連付けられているフォームのみを公開します。 参照された Dll で宣言されているフォームへのアクセスは提供されません。 DLL を提供するフォームにアクセスするには、として書き込まれる、フォームの修飾名を使用する必要があります*DllName*.*フォーム名*です。  
  
 使用することができます、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>アプリケーションのすべての開いているフォームのコレクションを取得するプロパティです。  
  
 オブジェクトとそのプロパティは、Windows アプリケーションでのみ使用できます。  
  
## <a name="properties"></a>プロパティ  
 各プロパティ、`My.Forms`オブジェクトが現在のプロジェクトにフォームのインスタンスへのアクセスを提供します。 プロパティの名前は、プロパティにアクセスする、フォームの名前と同じとプロパティの型が、フォームの型と同じです。  
  
> [!NOTE]
>  名前の競合がある場合、フォームにアクセスするプロパティ名は*RootNamespace*_*Namespace*\_*フォーム*です。 たとえば、という 2 つのフォーム`Form1.`かどうか、ルート名前空間でこれらの形式の 1 つは`WindowsApplication1`と名前空間に`Namespace1`、通じてそのフォームにアクセス`My.Forms.WindowsApplication1_Namespace1_Form1`です。  
  
 `My.Forms`オブジェクトは、スタートアップ時に作成されたアプリケーションのメイン フォームのインスタンスへのアクセスを提供します。 その他のすべてのフォーム、`My.Forms`へのアクセスがおよび格納時にオブジェクトをフォームの新しいインスタンスを作成します。 そのプロパティにアクセスしようとするとは、フォームのインスタンスを返します。  
  
 割り当てることによって、フォームの破棄する`Nothing`そのフォームのプロパティにします。 プロパティ set アクセス操作子の呼び出し、<xref:System.Windows.Forms.Form.Close%2A>フォーム、し、割り当てますメソッド`Nothing`に格納されている値。 以外の任意の値を割り当てる場合`Nothing`プロパティの setter がスローされます、<xref:System.ArgumentException>例外。  
  
 プロパティかどうかをテストすることができます、`My.Forms`オブジェクトを使用して、フォームのインスタンスが格納されて、`Is`または`IsNot`演算子。 これらの演算子を使用するには、プロパティの値をチェックする`Nothing`です。  
  
> [!NOTE]
>  通常、`Is`または`IsNot`オペレーターが、比較を実行するプロパティの値を読み取ることがあります。 ただし場合、プロパティが現在格納`Nothing`プロパティ、フォームの新しいインスタンスを作成し、そのインスタンスを返します。 ただし、Visual Basic コンパイラがのプロパティを処理、`My.Forms`オブジェクトが異なることができ、`Is`または`IsNot`演算子をその値を変更することがなく、プロパティの状態を確認します。  
  
## <a name="example"></a>例  
 この例は、既定のタイトルを変更`SidebarMenu`フォーム。  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 この例を実行するため、プロジェクトがという名前のフォーム`SidebarMenu`です。 詳細については、次を参照してください。[する方法: Windows フォームをプロジェクトに追加](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)です。  
  
 このコードは、Windows アプリケーション プロジェクトでのみ動作します。  
  
## <a name="requirements"></a>要件  
  
### <a name="availability-by-project-type"></a>プロジェクトの種類別の可用性  
  
|プロジェクトの種類|使用可能|  
|---|---|  
|Windows アプリケーション|**はい**|  
|クラス ライブラリ|いいえ|  
|コンソール アプリケーション|いいえ|  
|Windows コントロール ライブラリ|いいえ|  
|Web コントロール ライブラリ|いいえ|  
|Windows サービス|いいえ|  
|Web サイト|いいえ|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [オブジェクト](../../../visual-basic/language-reference/objects/index.md)  
 [方法: Windows フォームをプロジェクトに追加します。](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [アプリケーション フォームへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
