---
title: Expressions1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18c64daca1532bb626a59e5f01528e207e6b6b87
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="expressions"></a><span data-ttu-id="13cae-102">式</span><span class="sxs-lookup"><span data-stu-id="13cae-102">Expressions</span></span>
<span data-ttu-id="13cae-103">Windows Workflow Foundation (WF) 式は、結果を返す任意のアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="13cae-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="13cae-104">すべての式アクティビティは、アクティビティの戻り値として <xref:System.Activities.Activity%601> という名前の <xref:System.Activities.OutArgument> プロパティを含む <xref:System.Activities.Activity%601.Result%2A> から間接的に派生します。</span><span class="sxs-lookup"><span data-stu-id="13cae-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="13cae-105"> には、幅広い式アクティビティが用意されています。式アクティビティは、演算子アクティビティを介して 1 つのワークフロー変数へアクセスできる <xref:System.Activities.Expressions.VariableValue%601> や <xref:System.Activities.Expressions.VariableReference%601> などの単純なアクティビティから、結果を生成するために Visual Basic 言語一式へアクセスできる <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> や <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> などの複雑なアクティビティまでさまざまです。</span><span class="sxs-lookup"><span data-stu-id="13cae-105"> ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="13cae-106">追加の式アクティビティは、<xref:System.Activities.CodeActivity%601> または <xref:System.Activities.NativeActivity%601> から派生して作成できます。</span><span class="sxs-lookup"><span data-stu-id="13cae-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="13cae-107">式の使用</span><span class="sxs-lookup"><span data-stu-id="13cae-107">Using Expressions</span></span>  
 <span data-ttu-id="13cae-108">ワークフロー デザイナーでは、Visual Basic プロジェクトのすべての式に <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> および <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601>、C# ワークフロー プロジェクトの式に <xref:Microsoft.CSharp.Activities.CSharpValue%601> および <xref:Microsoft.CSharp.Activities.CSharpReference%601> を使用します。</span><span class="sxs-lookup"><span data-stu-id="13cae-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13cae-109">ワークフロー プロジェクトでの C# 式のサポートは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で導入されました。</span><span class="sxs-lookup"><span data-stu-id="13cae-109">Support for C# expressions in workflow projects was introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="13cae-110">詳細については、次を参照してください。 [c# 式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="13cae-110">For more information, see [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="13cae-111">デザイナーによって生成されたワークフローは XAML に保存されます。XAML には、次の例のように、式が角かっこに囲まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="13cae-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
```xml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />  
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />  
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />  
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />  
  </Sequence.Variables>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Sequence>  
```  
  
 <span data-ttu-id="13cae-112">コードでワークフローを定義すると、任意の式アクティビティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="13cae-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="13cae-113">次のコードは、3 つの数を追加する演算子アクティビティの使用例です。</span><span class="sxs-lookup"><span data-stu-id="13cae-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new Add<int, int, int> {  
                    Left = new Add<int, int, int> {  
                        Left = new InArgument<int>(a),  
                        Right = new InArgument<int>(b)  
                    },  
                    Right = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 <span data-ttu-id="13cae-114">C# のラムダ式を使用すると、次の例のように、同じワークフローをよりコンパクトに表現できます。</span><span class="sxs-lookup"><span data-stu-id="13cae-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="13cae-115">次の例のように、Visual Basic の式アクティビティを使用してワークフローを表現することもできます。</span><span class="sxs-lookup"><span data-stu-id="13cae-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="13cae-116">カスタム式アクティビティによる使用可能な式の拡張</span><span class="sxs-lookup"><span data-stu-id="13cae-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="13cae-117">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] の式には、追加の式アクティビティを作成できる拡張性があります。</span><span class="sxs-lookup"><span data-stu-id="13cae-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="13cae-118">次のコードは、3 つの整数値の合計を返すアクティビティの例です。</span><span class="sxs-lookup"><span data-stu-id="13cae-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Activities;  
  
namespace ExpressionsDemo  
{  
    public sealed class AddThreeValues : CodeActivity<int>  
    {  
        public InArgument<int> Value1 { get; set; }  
        public InArgument<int> Value2 { get; set; }  
        public InArgument<int> Value3 { get; set; }  
  
        protected override int Execute(CodeActivityContext context)  
        {  
            return Value1.Get(context) +   
                   Value2.Get(context) +   
                   Value3.Get(context);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="13cae-119">次の例のように、この新しいアクティビティを使用して、3 つの値を追加した前のワークフローを書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="13cae-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new AddThreeValues() {  
                    Value1 = new InArgument<int>(a),  
                    Value2 = new InArgument<int>(b),  
                    Value3 = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="13cae-120"> 式を使用して、コードを参照してください[オーサリング ワークフロー、アクティビティ、および命令型コードを使用して式](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="13cae-120"> using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
