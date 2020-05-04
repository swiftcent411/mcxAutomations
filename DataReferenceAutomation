$('<form><h1 style="z-index:10000">Survey Name</h1><input type="text" style="z-index:10000" id="surveyName"><br><h1 style="z-index:10000">Survey Code</h1><input type="text" style="z-index:10000" id="surveyCode"><br><h1 style="z-index:10000">Reference Type</h1><input type="text" style="z-index:10000" id="referenceType"><br><h1 style="z-index:10000">Fallback Text</h1><input type="text" style="z-index:10000" id="fallbackText"><br></form>').dialog({

    modal: true,
    buttons: {
      'OK': function () {
        localStorage.removeItem('surveyName');
        localStorage.removeItem('surveyId');
        localStorage.removeItem('questionCount');
        localStorage.removeItem('arrowID');
        localStorage.removeItem('nextQi');
        localStorage.removeItem('surveyCode');
        localStorage.removeItem('referenceType');
        localStorage.removeItem('fallbackText');

        var name = $('input[id="surveyName"]').val();
        var surveyCode = $('input[id="surveyCode"]').val();
        var referenceType = $('input[id="referenceType"]').val();
        var fallbackText = $('input[id="fallbackText"]').val();
        localStorage.surveyName = name;
        $('#divSurveys .allegAccordionHeader.default').each(function(){
            if($(this).text() == localStorage.surveyName){
                localStorage.surveyId = $(this).next().attr('id');
                localStorage.questionCount =  $(this).closest('#divSurveys').find('input:radio:visible').length;
                localStorage.arrowID = $(this).index()+1;
                localStorage.nextQi = 0;
                localStorage.surveyCode = surveyCode;
                localStorage.referenceType = referenceType;
                localStorage.fallbackText = fallbackText;
            };
        });
        $(this).dialog('close');
        $('body > div.ui-dialog.ui-widget.ui-widget-content.ui-corner-all.ui-front.qa-createDataReferenceDialog.ui-dialog-buttons.ui-draggable.ui-resizable > div.ui-dialog-titlebar.ui-widget-header.ui-corner-all.ui-helper-clearfix.ui-draggable-handle > button').click();
        qArr = [];
        for(i=0;i<=(parseInt(localStorage.questionCount)-1);i++){
        
            $('#emailTemplateTokenField > div > div:nth-child(3) > div.cmToolboxGroupHeader > div > div').click();
           
            setTimeout(() => {
                $('#divSurveys > div:nth-child('+localStorage.arrowID+')').click(); 
            
                for(i=0;i<=$('#'+localStorage.surveyId+' input:radio').length-1;i++){
                    if(i == parseInt(localStorage.nextQi)) {
                           var nextQi = parseInt(localStorage.nextQi)+1;
                        $('#'+localStorage.surveyId+' input:radio:eq('+nextQi+')').click();
                        $('#'+localStorage.surveyId+' input:radio:eq('+nextQi+')').click();
                        localStorage.nextQi = nextQi;  
                        break;
                    };   
                };
                
                 $('#txtDataReferenceName').val(localStorage.surveyCode + '-' + localStorage.referenceType + '-' + $('#divSurveyQuestionSummary > div:nth-child(2)').text());
                 $('#txtDataReferenceCode').text('['+localStorage.surveyCode + '-' + localStorage.referenceType + '-' + $('#divSurveyQuestionSummary > div:nth-child(2)').text()+']');
                 qArr.push($('#txtDataReferenceCode').text());
                 $('#txtDataReferenceFallbackText').val(localStorage.fallbackText);
                 $('#selDataReferenceType').val(3);
                 $('#btnSaveDataReference').click();
            }, 10000);
            
        };   
      },
      'Cancel': function () {
        $(this).dialog('close');
      }
    }
  });
