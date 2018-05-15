---
title: カスタム式エディターの使用
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: 4eb39fbd51cf4f1914f7fdca545f9c9fd8e83240
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="656bd-102">カスタム式エディターの使用</span><span class="sxs-lookup"><span data-stu-id="656bd-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="656bd-103">カスタム式エディターを実装して、式の編集を多機能化したり単純化したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="656bd-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="656bd-104">たとえば、次のような場合にカスタム式エディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="656bd-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
-   <span data-ttu-id="656bd-105">再ホストされたワークフロー デザイナーで IntelliSense などの高度な編集機能をサポートする場合。</span><span class="sxs-lookup"><span data-stu-id="656bd-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="656bd-106">Visual Studio の既定の式エディターは、再ホストされたアプリケーションで使用できないために、この機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="656bd-106">This functionality must be provided because the default Visual Studio expression editor cannot be used in rehosted applications.</span></span>  
  
-   <span data-ttu-id="656bd-107">Visual Basic の学習または Visual Basic 式を処理するなどの必要はありません、ようには、式のビジネス アナリスト ユーザーのため、編集を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="656bd-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn Visual Basic or deal with Visual Basic expressions.</span></span>  
  
 <span data-ttu-id="656bd-108">カスタム式エディターを実装するには、次の 3 つの基本的な手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="656bd-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1.  <span data-ttu-id="656bd-109"><xref:System.Activities.Presentation.View.IExpressionEditorService> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="656bd-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="656bd-110">このインターフェイスは、式エディターの作成と破棄を管理します。</span><span class="sxs-lookup"><span data-stu-id="656bd-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2.  <span data-ttu-id="656bd-111"><xref:System.Activities.Presentation.View.IExpressionEditorInstance> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="656bd-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="656bd-112">このインターフェイスは、式エディター UI に UI を実装します。</span><span class="sxs-lookup"><span data-stu-id="656bd-112">This interface implements the UI for expression editing UI.</span></span>  
  
3.  <span data-ttu-id="656bd-113">再ホストされたワークフロー アプリケーションで <xref:System.Activities.Presentation.View.IExpressionEditorService> を公開します。</span><span class="sxs-lookup"><span data-stu-id="656bd-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="656bd-114">クラス ライブラリ内のカスタム式エディターを実装する</span><span class="sxs-lookup"><span data-stu-id="656bd-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="656bd-115">次のコードは、MyExpressionEditorService ライブラリ プロジェクトに含まれている `MyEditorService` インターフェイスを実装する (概念実証) <xref:System.Activities.Presentation.View.IExpressionEditorService> クラスのサンプル コードです。</span><span class="sxs-lookup"><span data-stu-id="656bd-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="656bd-116">MyExpressionEditorService ライブラリ プロジェクトの `MyExpressionEditorInstance` インターフェイスを実装する <xref:System.Activities.Presentation.View.IExpressionEditorInstance> クラスのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="656bd-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="656bd-117">WPF プロジェクトでカスタム式エディターを公開する</span><span class="sxs-lookup"><span data-stu-id="656bd-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="656bd-118">次のコードは、[!INCLUDE[avalon2](../../../includes/avalon2-md.md)] アプリケーションでデザイナーを再ホストする方法と、`MyEditorService` サービスを作成して公開する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="656bd-118">Here is the code that shows how to rehost the designer in a [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="656bd-119">このコードを使用する前に、avalon2 アプリケーションを含むプロジェクトから、MyExpressionEditorService ライブラリ プロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="656bd-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService   
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a><span data-ttu-id="656bd-120">メモ</span><span class="sxs-lookup"><span data-stu-id="656bd-120">Notes</span></span>  
 <span data-ttu-id="656bd-121">使用している場合、 **ExpressionTextBox**コントロール、カスタム アクティビティ デザイナーで必要はありません作成し、破棄を使用して式エディターに、<xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A>と<xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A>のメソッド、<xref:System.Activities.Presentation.View.IExpressionEditorService>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="656bd-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="656bd-122"><xref:System.Activities.Presentation.View.ExpressionTextBox> クラスによってこの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="656bd-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656bd-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="656bd-123">See Also</span></span>  
 <xref:System.Activities.Presentation.View.IExpressionEditorService>  
 <xref:System.Activities.Presentation.View.IExpressionEditorInstance>  
 [<span data-ttu-id="656bd-124">カスタム アクティビティ デザイナーでの ExpressionTextBox の使用</span><span class="sxs-lookup"><span data-stu-id="656bd-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
