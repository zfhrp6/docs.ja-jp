---
title: "方法 : Windows フォーム BindingSource を使用して Web サービスにバインドする"
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
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a647f688f0ae8566a7129982e78e3d9503bee6af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="4e0a8-102">方法 : Windows フォーム BindingSource を使用して Web サービスにバインドする</span><span class="sxs-lookup"><span data-stu-id="4e0a8-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="4e0a8-103">XML Web サービスを呼び出して取得した結果に対して Windows フォーム コントロールをバインドする場合は、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="4e0a8-104">この手順は、<xref:System.Windows.Forms.BindingSource> コンポーネントを型にバインディングする場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="4e0a8-105">Web サービスが公開するメソッドおよび型を含むクライアント側プロキシを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="4e0a8-106">クライアント側プロキシは、Web サービス (.asmx) 自体またはその Web サービス記述言語 (WSDL: Web Services Description Language) ファイルから生成できます。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="4e0a8-107">また、クライアント側プロキシでは Web サービスが使用する複合型のフィールドをパブリック プロパティとして公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="4e0a8-108">その後、Web サービス プロキシ内で公開された型のいずれかに <xref:System.Windows.Forms.BindingSource> をバインドします。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="4e0a8-109">クライアント側プロキシを作成してバインドするには</span><span class="sxs-lookup"><span data-stu-id="4e0a8-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="4e0a8-110">適切な名前空間を使用して、任意のディレクトリに Windows フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="4e0a8-111">フォームに <xref:System.Windows.Forms.BindingSource> コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="4e0a8-112">[!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] コマンド プロンプトを開き、フォームと同じディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="4e0a8-113">WSDL ツールを使用して、`wsdl`、および Web サービスの .asmx ファイルまたは WSDL ファイルの URL を入力し、次にアプリケーションの名前空間を入力し、使用している言語 (これはオプション) を入力します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="4e0a8-114">次のコード例では、http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx にある Web サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-114">The following code example uses the Web service located at http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span></span> <span data-ttu-id="4e0a8-115">たとえば、C# の型の場合は `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`、Visual Basic の型の場合は `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB` です。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="4e0a8-116">パスを引数として WSDL ツールに渡すことで、指定した言語で、アプリケーションと同じディレクトリおよび名前空間にクライアント側プロキシが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="4e0a8-117">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] を使用している場合は、プロジェクトにファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-117">If you are using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], add the file to your project.</span></span>  
  
5.  <span data-ttu-id="4e0a8-118">バインド先のクライアント側プロキシの型を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="4e0a8-119">これは、通常、Web サービスによって提供されるメソッドが返す型です。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="4e0a8-120">選択した型のフィールドは、バインド用にパブリック プロパティとして公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="4e0a8-121"><xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティに、Web サービスのクライアント側プロキシに含まれる任意の型を設定します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="4e0a8-122">Web サービスにバインドされた BindingSource にコントロールをバインドするには</span><span class="sxs-lookup"><span data-stu-id="4e0a8-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="4e0a8-123">コントロールを <xref:System.Windows.Forms.BindingSource> にバインドし、Web サービスの任意の型のパブリック プロパティをパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="4e0a8-124">例</span><span class="sxs-lookup"><span data-stu-id="4e0a8-124">Example</span></span>  
 <span data-ttu-id="4e0a8-125"><xref:System.Windows.Forms.BindingSource> コンポーネントを Web サービスにバインドし、テキスト ボックスを <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドするコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="4e0a8-126">ボタンをクリックすると、Web サービス メソッドが呼び出され、結果が `textbox1` に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e0a8-127">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="4e0a8-127">Compiling the Code</span></span>  
 <span data-ttu-id="4e0a8-128">これは、`Main` メソッドを含む完全な例であり、クライアント側プロキシのコードを短縮したバージョンです。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="4e0a8-129">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-129">This example requires:</span></span>  
  
-   <span data-ttu-id="4e0a8-130">System、System.Drawing、System.Web.Services、System.Windows.Forms、および System.Xml の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="4e0a8-131">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-131">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4e0a8-132">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-132">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="4e0a8-133">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e0a8-133">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e0a8-134">参照</span><span class="sxs-lookup"><span data-stu-id="4e0a8-134">See Also</span></span>  
 [<span data-ttu-id="4e0a8-135">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4e0a8-135">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="4e0a8-136">方法: Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="4e0a8-136">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
