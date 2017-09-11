---
title: "方法 : My 名前空間を使用する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 56577ff61c3f637c8e5a0969ae75d65d24ddaef7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="f483f-102">方法 : My 名前空間を使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f483f-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="f483f-103"><xref:Microsoft.VisualBasic.MyServices> 名前空間 (Visual Basic では `My`) を使用すると、いくつもの .NET Framework クラスに簡単かつ直感的にアクセスでき、コンピューター、アプリケーション、設定、リソースなどと対話するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="f483f-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="f483f-104">`MyServices` 名前空間は、もともとは Visual Basic で使用するものとして設計されましたが、C# アプリケーションでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f483f-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="f483f-105">Visual Basic で `MyServices` 名前空間を使用する方法の詳細については、「[Development with My](../../../visual-basic/developing-apps/development-with-my/index.md)」 (My を使用した開発) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f483f-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="f483f-106">参照の追加</span><span class="sxs-lookup"><span data-stu-id="f483f-106">Adding a Reference</span></span>  
 <span data-ttu-id="f483f-107">`MyServices` クラスをソリューションで使用する前に、Visual Basic ライブラリへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f483f-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="f483f-108">Visual Basic ライブラリへの参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="f483f-108">To add a reference to the Visual Basic library</span></span>  
  
1.  <span data-ttu-id="f483f-109">**ソリューション エクスプローラー**で、**[参照設定]** ノードを右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f483f-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="f483f-110">**[参照設定]** ダイアログ ボックスが表示されたら、一覧を下にスクロールし、Microsoft.VisualBasic.dll を選択します。</span><span class="sxs-lookup"><span data-stu-id="f483f-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="f483f-111">プログラムの先頭の `using` セクションに次の行を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="f483f-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     <span data-ttu-id="f483f-112">[!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f483f-112">[!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f483f-113">例</span><span class="sxs-lookup"><span data-stu-id="f483f-113">Example</span></span>  
 <span data-ttu-id="f483f-114">次の例では、`MyServices` 名前空間に含まれているさまざまな静的メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f483f-114">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="f483f-115">このコードをコンパイルするには、Microsoft.VisualBasic.DLL への参照をプロジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f483f-115">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 <span data-ttu-id="f483f-116">[!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f483f-116">[!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]</span></span>  
  
 <span data-ttu-id="f483f-117">`MyServices` 名前空間のクラスの中には C# アプリケーションから呼び出すことができないクラスもあります。たとえば、<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> クラスは、C# と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="f483f-117">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="f483f-118">そのような場合は、同様に VisualBasic.dll に含まれている <xref:Microsoft.VisualBasic.FileIO.FileSystem> を構成する静的メソッドを代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f483f-118">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="f483f-119">このようなメソッドを使用してディレクトリを複製する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f483f-119">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 <span data-ttu-id="f483f-120">[!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f483f-120">[!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f483f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f483f-121">See Also</span></span>  
 <span data-ttu-id="f483f-122">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f483f-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f483f-123">[名前空間](../../../csharp/programming-guide/namespaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="f483f-123">[Namespaces](../../../csharp/programming-guide/namespaces/index.md) </span></span>  
 [<span data-ttu-id="f483f-124">名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="f483f-124">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)

