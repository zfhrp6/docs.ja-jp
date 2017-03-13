---
title: "My.Forms Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.Forms"
  - "My.MyProject.Forms"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Forms object"
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# My.Forms Object
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

現在のプロジェクト内で宣言されている各 Windows フォームのインスタンスにアクセスするためのプロパティを提供します。  
  
## 解説  
 `My.Forms` オブジェクトは、現在のプロジェクト内の各フォームのインスタンスを提供します。  プロパティの名前は、そのプロパティのアクセス先のフォームと同じ名前になります。  フォームをプロジェクトに追加する方法については、「[How to: Add Windows Forms to a Project](http://msdn.microsoft.com/ja-jp/3d7bb25f-fd90-47cf-9378-fa0d764686c1)」を参照してください。  
  
 `My.Forms` オブジェクトによって提供されるフォームにアクセスするには、そのフォームの名前を修飾子なしで使用します。  このプロパティ名はフォームの型名と同じになるので、まるで既定のインスタンスがあるかのようにしてフォームにアクセスできます。  たとえば、`My.Forms.Form1.Show` は `Form1.Show` と同じ意味です。  
  
 `My.Forms` オブジェクトは、現在のプロジェクトに関連付けられているフォームのみを公開します。  参照された DLL 内で宣言されているフォームにはアクセスできません。  DLL 内で参照されているフォームにアクセスするには、*DllName*.*FormName* という形式の修飾名を使用する必要があります。  
  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> プロパティを使用すると、アプリケーションの現在開かれているすべてのフォームのコレクションを取得できます。  
  
 このオブジェクトとプロパティは、Windows アプリケーションでのみ使用できます。  
  
## プロパティ  
 `My.Forms` オブジェクトのプロパティを使用すると、現在のプロジェクト内のフォームのインスタンスにアクセスできます。  プロパティの名前はそのプロパティがアクセスするフォームの名前と同じになり、プロパティの型はフォームの型と同じになります。  
  
> [!NOTE]
>  名前の衝突が存在する場合、フォームにアクセスするためのプロパティ名は *RootNamespace*\_*Namespace*\_*FormName* になります。  たとえば、`Form1.` という名前のフォームが 2 つあるとします。一方のフォームがルート名前空間 `WindowsApplication1` 内の名前空間 `Namespace1` にある場合、このフォームにアクセスするには `My.Forms.WindowsApplication1_Namespace1_Form1` を使用します。  
  
 `My.Forms` オブジェクトは、アプリケーションの起動時に作成されたメイン フォームのインスタンスへのアクセスを提供します。  他のフォームについては、フォームへのアクセスが発生したときに `My.Forms` オブジェクトがそのフォームの新しいインスタンスを作成して格納します。  以降は、そのプロパティにアクセスするとフォームのインスタンスが返されます。  
  
 フォームを破棄するには、そのフォームを表すプロパティに `Nothing` を代入します。  このプロパティ Set アクセス操作子が対応するフォームの <xref:System.Windows.Forms.Form.Close%2A> メソッドを呼び出し、格納されている値に `Nothing` を代入します。  このプロパティに `Nothing` 以外の値を代入した場合は、setter が <xref:System.ArgumentException> 例外をスローします。  
  
 `My.Forms` オブジェクトのプロパティにフォームのインスタンスが格納されているかどうかを調べるには、`Is` または `IsNot` 演算子を使用します。  これらの演算子を使用して、プロパティの値が `Nothing` かどうかを確認します。  
  
> [!NOTE]
>  通常は、`Is` または `IsNot` 演算子が比較を実行するためには、プロパティの値を読み取る必要があります。  しかし、プロパティの現在の値が `Nothing` である場合は、値を読み取ろうとするとフォームの新しいインスタンスが作成され、そのインスタンスが返されてしまいます。  そこで、Visual Basic コンパイラは `My.Forms` オブジェクトのプロパティを特別扱いとし、`Is` または `IsNot` 演算子がプロパティの値を変更せずにプロパティのステータスを確認できるようにしています。  
  
## 使用例  
 この例では、既定の `SidebarMenu` フォームのタイトルを変更します。  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 この例を実行するには、`SidebarMenu` という名前のフォームがプロジェクト内に含まれている必要があります。  詳細については、「[How to: Add Windows Forms to a Project](http://msdn.microsoft.com/ja-jp/3d7bb25f-fd90-47cf-9378-fa0d764686c1)」を参照してください。  
  
 このコードは Windows アプリケーション プロジェクトでのみ有効です。  
  
## 要件  
  
### プロジェクトの種類ごとの可用性  
  
|||  
|-|-|  
|プロジェクトの種類|可用性|  
|Windows アプリケーション|**○**|  
|クラス ライブラリ|Ｘ|  
|コンソール アプリケーション|Ｘ|  
|Windows コントロール ライブラリ|Ｘ|  
|Web コントロール ライブラリ|Ｘ|  
|Windows サービス|Ｘ|  
|Web サイト|Ｘ|  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Form.Close%2A>   
 [Objects](../../../visual-basic/language-reference/objects/index.md)   
 [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/ja-jp/3d7bb25f-fd90-47cf-9378-fa0d764686c1)   
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Accessing Application Forms](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)