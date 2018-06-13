---
title: '方法 : Windows フォーム BindingSource を使用して Web サービスにバインドする'
ms.date: 03/30/2017
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
ms.openlocfilehash: 5a5db651b0690aae393666124c8d33402d57a189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531401"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="16f27-102">方法 : Windows フォーム BindingSource を使用して Web サービスにバインドする</span><span class="sxs-lookup"><span data-stu-id="16f27-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="16f27-103">XML Web サービスを呼び出して取得した結果に対して Windows フォーム コントロールをバインドする場合は、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="16f27-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="16f27-104">この手順は、<xref:System.Windows.Forms.BindingSource> コンポーネントを型にバインディングする場合と似ています。</span><span class="sxs-lookup"><span data-stu-id="16f27-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="16f27-105">Web サービスが公開するメソッドおよび型を含むクライアント側プロキシを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16f27-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="16f27-106">クライアント側プロキシは、Web サービス (.asmx) 自体またはその Web サービス記述言語 (WSDL: Web Services Description Language) ファイルから生成できます。</span><span class="sxs-lookup"><span data-stu-id="16f27-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="16f27-107">また、クライアント側プロキシでは Web サービスが使用する複合型のフィールドをパブリック プロパティとして公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16f27-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="16f27-108">その後、Web サービス プロキシ内で公開された型のいずれかに <xref:System.Windows.Forms.BindingSource> をバインドします。</span><span class="sxs-lookup"><span data-stu-id="16f27-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="16f27-109">クライアント側プロキシを作成してバインドするには</span><span class="sxs-lookup"><span data-stu-id="16f27-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="16f27-110">適切な名前空間を使用して、任意のディレクトリに Windows フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="16f27-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="16f27-111">フォームに <xref:System.Windows.Forms.BindingSource> コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="16f27-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="16f27-112">[!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] コマンド プロンプトを開き、フォームと同じディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="16f27-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="16f27-113">WSDL ツールを使用して、`wsdl`、および Web サービスの .asmx ファイルまたは WSDL ファイルの URL を入力し、次にアプリケーションの名前空間を入力し、使用している言語 (これはオプション) を入力します。</span><span class="sxs-lookup"><span data-stu-id="16f27-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="16f27-114">次のコード例にある Web サービスを使用してhttp://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmxです。</span><span class="sxs-lookup"><span data-stu-id="16f27-114">The following code example uses the Web service located at http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span></span> <span data-ttu-id="16f27-115">たとえば、C# の型の場合は `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`、Visual Basic の型の場合は `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB` です。</span><span class="sxs-lookup"><span data-stu-id="16f27-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="16f27-116">パスを引数として WSDL ツールに渡すことで、指定した言語で、アプリケーションと同じディレクトリおよび名前空間にクライアント側プロキシが生成されます。</span><span class="sxs-lookup"><span data-stu-id="16f27-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="16f27-117">Visual Studio を使用している場合、ファイルをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="16f27-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5.  <span data-ttu-id="16f27-118">バインド先のクライアント側プロキシの型を選択します。</span><span class="sxs-lookup"><span data-stu-id="16f27-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="16f27-119">これは、通常、Web サービスによって提供されるメソッドが返す型です。</span><span class="sxs-lookup"><span data-stu-id="16f27-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="16f27-120">選択した型のフィールドは、バインド用にパブリック プロパティとして公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16f27-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="16f27-121"><xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティに、Web サービスのクライアント側プロキシに含まれる任意の型を設定します。</span><span class="sxs-lookup"><span data-stu-id="16f27-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="16f27-122">Web サービスにバインドされた BindingSource にコントロールをバインドするには</span><span class="sxs-lookup"><span data-stu-id="16f27-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="16f27-123">コントロールを <xref:System.Windows.Forms.BindingSource> にバインドし、Web サービスの任意の型のパブリック プロパティをパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="16f27-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="16f27-124">例</span><span class="sxs-lookup"><span data-stu-id="16f27-124">Example</span></span>  
 <span data-ttu-id="16f27-125"><xref:System.Windows.Forms.BindingSource> コンポーネントを Web サービスにバインドし、テキスト ボックスを <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドするコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="16f27-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="16f27-126">ボタンをクリックすると、Web サービス メソッドが呼び出され、結果が `textbox1` に表示されます。</span><span class="sxs-lookup"><span data-stu-id="16f27-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="16f27-127">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="16f27-127">Compiling the Code</span></span>  
 <span data-ttu-id="16f27-128">これは、`Main` メソッドを含む完全な例であり、クライアント側プロキシのコードを短縮したバージョンです。</span><span class="sxs-lookup"><span data-stu-id="16f27-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="16f27-129">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="16f27-129">This example requires:</span></span>  
  
-   <span data-ttu-id="16f27-130">System、System.Drawing、System.Web.Services、System.Windows.Forms、および System.Xml の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="16f27-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="16f27-131">コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="16f27-131">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="16f27-132">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="16f27-132">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="16f27-133">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="16f27-133">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f27-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="16f27-134">See Also</span></span>  
 [<span data-ttu-id="16f27-135">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="16f27-135">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="16f27-136">方法: Windows フォーム コントロールを型にバインドする</span><span class="sxs-lookup"><span data-stu-id="16f27-136">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
