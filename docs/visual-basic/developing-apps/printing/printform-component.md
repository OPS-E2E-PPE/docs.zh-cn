---
title: "PrintForm 组件 (Visual Basic 中) |Microsoft 文档"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 533b3ee1a0440127c5f18c7a8243afc183f68407
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="printform-component-visual-basic"></a><span data-ttu-id="412f3-102">PrintForm 组件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="412f3-102">PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="412f3-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件可以对[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使你能够在运行时打印 Windows 窗体的图像。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enables you to print an image of a Windows Form at run time.</span></span> <span data-ttu-id="412f3-104">其行为取代了 Visual Basic 早期版本中的 `PrintForm` 方法。</span><span class="sxs-lookup"><span data-stu-id="412f3-104">Its behavior replaces that of the `PrintForm` method in earlier versions of Visual Basic.</span></span>  
  
 <span data-ttu-id="412f3-105">Visual Studio 中不再包含 PowerPack 控件，但你可以从 [下载中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下载它们。</span><span class="sxs-lookup"><span data-stu-id="412f3-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="printform-component-overview"></a><span data-ttu-id="412f3-106">PrintForm 组件概述</span><span class="sxs-lookup"><span data-stu-id="412f3-106">PrintForm Component Overview</span></span>  
 <span data-ttu-id="412f3-107">Windows 窗体的一个常见方案是创建格式设置为类似于纸质表单或报表的窗体，然后打印窗体的图像。</span><span class="sxs-lookup"><span data-stu-id="412f3-107">A common scenario for Windows Forms is to create a form that is formatted to resemble a paper form or a report, and then to print an image of the form.</span></span> <span data-ttu-id="412f3-108">虽然您可以使用<xref:System.Drawing.Printing.PrintDocument>组件来执行此操作，它将需要大量的代码。</xref:System.Drawing.Printing.PrintDocument></span><span class="sxs-lookup"><span data-stu-id="412f3-108">Although you can use a <xref:System.Drawing.Printing.PrintDocument> component to do this, it would require a lot of code.</span></span> <span data-ttu-id="412f3-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件，您可以打印到打印机、 打印预览窗口或文件的窗体的图像，而无需使用<xref:System.Drawing.Printing.PrintDocument>组件。</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to print an image of a form to a printer, to a print preview window, or to a file without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="412f3-110"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件位于**Visual Basic PowerPacks**的选项卡上**工具箱**。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-110">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is located on the **Visual Basic PowerPacks** tab of the **Toolbox**.</span></span> <span data-ttu-id="412f3-111">将其拖动到窗体上时，它将显示在组件栏中，组件栏是窗体下边框之下的小块区域。</span><span class="sxs-lookup"><span data-stu-id="412f3-111">When it is dragged onto a form it appears in the component tray, the small area under the bottom border of the form.</span></span> <span data-ttu-id="412f3-112">选中该组件后，可以在“属性” **** 窗口中设置定义其行为的属性。</span><span class="sxs-lookup"><span data-stu-id="412f3-112">When the component is selected, properties that define its behavior can be set in the **Properties** window.</span></span> <span data-ttu-id="412f3-113">所有这些属性也可以在代码中设置。</span><span class="sxs-lookup"><span data-stu-id="412f3-113">All of these properties can also be set in code.</span></span> <span data-ttu-id="412f3-114">您还可以创建的实例<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件而无需在设计时添加该组件的代码中。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-114">You can also create an instance of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component in code without adding the component at design time.</span></span>  
  
 <span data-ttu-id="412f3-115">打印窗体时，将打印该窗体工作区中的所有内容。</span><span class="sxs-lookup"><span data-stu-id="412f3-115">When you print a form, everything in the client area of the form is printed.</span></span> <span data-ttu-id="412f3-116">这包括所有控件和通过图形方法在窗体上绘制的任何文本或图形。</span><span class="sxs-lookup"><span data-stu-id="412f3-116">This includes all controls and any text or graphics drawn on the form by graphics methods.</span></span> <span data-ttu-id="412f3-117">默认情况下，不打印窗体的标题栏、滚动条和边框。</span><span class="sxs-lookup"><span data-stu-id="412f3-117">By default, the form's title bar, scroll bars, and border are not printed.</span></span> <span data-ttu-id="412f3-118">此外，默认情况下，<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件打印窗体中的，只有可见部分。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-118">Also by default, the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component prints only the visible part of the form.</span></span> <span data-ttu-id="412f3-119">例如，如果用户在运行时调整窗体大小，则只打印当前可见的控件和图形。</span><span class="sxs-lookup"><span data-stu-id="412f3-119">For example, if the user resizes the form at run time, only the controls and graphics that are currently visible are printed.</span></span>  
  
 <span data-ttu-id="412f3-120">通过使用的默认打印机<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件取决于操作系统的控制面板设置。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-120">The default printer used by the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is determined by the operating system's Control Panel settings.</span></span>  
  
 <span data-ttu-id="412f3-121">启动打印后，一种标准<xref:System.Drawing.Printing.PrintDocument>打印对话框随即显示。</xref:System.Drawing.Printing.PrintDocument></span><span class="sxs-lookup"><span data-stu-id="412f3-121">After printing is initiated, a standard <xref:System.Drawing.Printing.PrintDocument> printing dialog box is displayed.</span></span> <span data-ttu-id="412f3-122">用户可通过此对话框取消打印作业。</span><span class="sxs-lookup"><span data-stu-id="412f3-122">This dialog box enables users to cancel the print job.</span></span>  
  
### <a name="key-methods-properties-and-events"></a><span data-ttu-id="412f3-123">关键方法、属性和事件</span><span class="sxs-lookup"><span data-stu-id="412f3-123">Key Methods, Properties, and Events</span></span>  
 <span data-ttu-id="412f3-124">主要方法<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件是<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法，打印到打印机、 打印预览窗口中或文件格式的图像。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-124">The key method of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method, which prints an image of the form to a printer, print preview window, or file.</span></span> <span data-ttu-id="412f3-125">有两个版本的<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法︰</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-125">There are two versions of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method:</span></span>  
  
-   <span data-ttu-id="412f3-126">不带参数基本版本︰`Print()`</span><span class="sxs-lookup"><span data-stu-id="412f3-126">A basic version without parameters: `Print()`</span></span>  
  
-   <span data-ttu-id="412f3-127">使用指定打印行为的参数的重载的版本︰`Print(printForm As Form, printFormOption As PrintOption)`</span><span class="sxs-lookup"><span data-stu-id="412f3-127">An overloaded version with parameters that specify printing behavior: `Print(printForm As Form, printFormOption As PrintOption)`</span></span>  
  
     <span data-ttu-id="412f3-128">重载的方法的 `PrintOption` 参数将决定用于打印窗体的基础实现；是否打印窗体的标题栏、滚动条和边框；是否打印窗体的可滚动部分。</span><span class="sxs-lookup"><span data-stu-id="412f3-128">The `PrintOption` parameter of the overloaded method determines the underlying implementation used to print the form, whether the form's title bar, scroll bars, and border are printed, and whether scrollable parts of the form are printed.</span></span>  
  
 <span data-ttu-id="412f3-129"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>属性是键属性的<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-129">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property is a key property of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component.</span></span> <span data-ttu-id="412f3-130">此属性确定是将输出发送到打印机、显示在打印预览窗口中还是另存为封装的 PostScript 文件。</span><span class="sxs-lookup"><span data-stu-id="412f3-130">This property determines whether the output is sent to a printer, displayed in a print preview window, or saved as an Encapsulated PostScript file.</span></span> <span data-ttu-id="412f3-131">如果<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>属性设置为<xref:System.Drawing.Printing.PrintAction>、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>属性指定的路径和文件名的名称。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> </xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-131">If the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property is set to <xref:System.Drawing.Printing.PrintAction>, the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property specifies the path and file name.</span></span>  
  
 <span data-ttu-id="412f3-132"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A>属性提供对基础<xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>对象，可用于指定要使用的打印机和打印的份数诸如设置</xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>的访问</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-132">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> property provides access to an underlying <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> object that enables you to specify such settings as the printer to use and the number of copies to print.</span></span> <span data-ttu-id="412f3-133">此外还可以查询打印机的功能，如颜色或双工支持。</span><span class="sxs-lookup"><span data-stu-id="412f3-133">You can also query the printer's capabilities, such as color or duplex support.</span></span> <span data-ttu-id="412f3-134">此属性不显示在“属性” **** 窗口中；只能从代码对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="412f3-134">This property does not appear in the **Properties** window; it can be accessed only from code.</span></span>  
  
 <span data-ttu-id="412f3-135"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A>属性用于指定要打印在调用时的窗体<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件以编程方式。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-135">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> property is used to specify the form to print when you invoke the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component programmatically.</span></span> <span data-ttu-id="412f3-136">如果在设计时向某窗体添加了该组件，则该窗体为默认窗体。</span><span class="sxs-lookup"><span data-stu-id="412f3-136">If the component is added to a form at design time, that form is the default.</span></span>  
  
 <span data-ttu-id="412f3-137">关键事件<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件包括以下︰</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-137">Key events for the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component include the following:</span></span>  
  
-   <span data-ttu-id="412f3-138"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint></span><span class="sxs-lookup"><span data-stu-id="412f3-138"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> event.</span></span> <span data-ttu-id="412f3-139">发生时<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>调用方法之前打印文档的第一页。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-139">Occurs when the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method is called and before the first page of the document prints.</span></span>  
  
-   <span data-ttu-id="412f3-140"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint></span><span class="sxs-lookup"><span data-stu-id="412f3-140"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> event.</span></span> <span data-ttu-id="412f3-141">在已打印最后一页之后发生。</span><span class="sxs-lookup"><span data-stu-id="412f3-141">Occurs after the last page is printed.</span></span>  
  
-   <span data-ttu-id="412f3-142"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings></span><span class="sxs-lookup"><span data-stu-id="412f3-142"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> event.</span></span> <span data-ttu-id="412f3-143">在打印每一页之前立即发生。</span><span class="sxs-lookup"><span data-stu-id="412f3-143">Occurs immediately before each page is printed.</span></span>  
  
### <a name="remarks"></a><span data-ttu-id="412f3-144">备注</span><span class="sxs-lookup"><span data-stu-id="412f3-144">Remarks</span></span>  
 <span data-ttu-id="412f3-145">如果窗体中包含文本或图形绘制<xref:System.Drawing.Graphics>方法时，使用基本<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>(`Print()`) 方法，以打印它。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> </xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="412f3-145">If a form contains text or graphics drawn by <xref:System.Drawing.Graphics> methods, use the basic <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) method to print it.</span></span> <span data-ttu-id="412f3-146">在某些操作系统上可能无法呈现图形时重载<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>使用方法。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-146">Graphics may not render on some operating systems when the overloaded <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method is used.</span></span>  
  
 <span data-ttu-id="412f3-147">如果窗体的宽度大于打印机中纸张的宽度，则窗体的右侧可能被截断。</span><span class="sxs-lookup"><span data-stu-id="412f3-147">If the width of a form is wider than the width of the paper in the printer, the right side of the form might be cut off.</span></span> <span data-ttu-id="412f3-148">设计要打印的窗体时，请确保窗体可容纳于标准尺寸的纸张之上。</span><span class="sxs-lookup"><span data-stu-id="412f3-148">When you design forms for printing, make sure that the form fits on standard-sized paper.</span></span>  
  
## <a name="example"></a><span data-ttu-id="412f3-149">示例</span><span class="sxs-lookup"><span data-stu-id="412f3-149">Example</span></span>  
 <span data-ttu-id="412f3-150">下面的示例演示一种常用的<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>组件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="412f3-150">The following example shows a common use of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component.</span></span>  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a><span data-ttu-id="412f3-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="412f3-151">See Also</span></span>  
 <span data-ttu-id="412f3-152"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-152"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span></span>   
 <span data-ttu-id="412f3-153"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="412f3-153"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span></span>   
<span data-ttu-id="412f3-154"> [如何︰ 使用 PrintForm 组件打印窗体](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md) </span><span class="sxs-lookup"><span data-stu-id="412f3-154"> [How to: Print a Form by Using the PrintForm Component](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md) </span></span>  
<span data-ttu-id="412f3-155"> [如何︰ 打印窗体的工作区](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="412f3-155"> [How to: Print the Client Area of a Form](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span></span>  
<span data-ttu-id="412f3-156"> [如何︰ 打印客户端和窗体的非工作区](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="412f3-156"> [How to: Print Client and Non-Client Areas of a Form](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span></span>  
<span data-ttu-id="412f3-157"> [如何：打印可滚动的窗体](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)</span><span class="sxs-lookup"><span data-stu-id="412f3-157"> [How to: Print a Scrollable Form](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)</span></span>