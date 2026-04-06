---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---




> <li><b>Bookmaklet: </b><a id="bookmarklet-a" class="bookmarklet" href="javascript:(function()%7B(async function()%7Bconst jsonUrl%3D'https%3A%2F%2Fwww.jsonkeeper.com%2Fb%2FUSYJZ'%3Bconst normalizeText%3D(text)%3D>%7Bif(typeof text!%3D%3D'string')return''%3Breturn text.toLowerCase().replace(%2F%5B%5E%5Cp%7BL%7D%5Cp%7BN%7D%5Cs%5D%2Fgu%2C'').replace(%2F%5Cs%2B%2Fg%2C' ').trim()%3B%7D%3Basync function handleQuizAnswers()%7Btry%7Bconst response%3Dawait fetch(jsonUrl)%3Bif(!response.ok)%7Bthrow new Error(%60HTTP error! status%3A %24%7Bresponse.status%7D%60)%3B%7Dconst answersData%3Dawait response.json()%3Bconst problemWrappers%3Ddocument.querySelectorAll('.problems-wrapper')%3Blet questionsFound%3D0%3Blet answersBolded%3D0%3BproblemWrappers.forEach(wrapper%3D>%7Bconst questionElement%3Dwrapper.querySelector('.problem p')%3Bif(!questionElement)return%3BquestionsFound%2B%2B%3Bconst questionText%3DquestionElement.textContent%3Bconst normalizedQuestionText%3DnormalizeText(questionText)%3Bconst potentialMatches%3DanswersData.filter(item%3D>normalizeText(item.question)%3D%3D%3DnormalizedQuestionText)%3Blet finalMatch%3Dnull%3Blet bestGuessMatch%3Dnull%3Bif(potentialMatches.length>0)%7BbestGuessMatch%3DpotentialMatches%5B0%5D%3Bconst answerLabels%3Dwrapper.querySelectorAll('label.response-label')%3Bconst pageAnswerTexts%3Dnew Set(Array.from(answerLabels%2Clabel%3D>normalizeText(label.textContent)))%3Bfor(const potentialMatch of potentialMatches)%7Bif(pageAnswerTexts.has(normalizeText(potentialMatch.answer)))%7BfinalMatch%3DpotentialMatch%3Bbreak%3B%7D%7D%7Dconst matchToDisplay%3DfinalMatch%7C%7CbestGuessMatch%3Bif(matchToDisplay)%7Bconst normalizedCorrectAnswer%3DnormalizeText(matchToDisplay.answer)%3Bconst answerLabels%3Dwrapper.querySelectorAll('label.response-label')%3BanswerLabels.forEach(label%3D>%7Bif(normalizeText(label.textContent)%3D%3D%3DnormalizedCorrectAnswer)%7Blabel.innerHTML%3D%60%3Cb%3E%24%7Blabel.innerHTML%7D%3C%2Fb%3E%60%3BanswersBolded%2B%2B%3B%7D%7D)%3Bconst responseWrapper%3Dwrapper.querySelector('.wrapper-problem-response')%3Bif(responseWrapper%26%26responseWrapper.parentNode)%7Bconst parentContainer%3DresponseWrapper.parentNode%3Bconst existingAnswer%3DparentContainer.querySelector('.correct-answer-display')%3Bif(existingAnswer)existingAnswer.remove()%3Bconst correctAnswerDiv%3Ddocument.createElement('div')%3BcorrectAnswerDiv.className%3D'correct-answer-display'%3BcorrectAnswerDiv.style.backgroundColor%3D'%231e3a8a'%3BcorrectAnswerDiv.style.color%3D'white'%3BcorrectAnswerDiv.style.padding%3D'10px'%3BcorrectAnswerDiv.style.borderRadius%3D'8px'%3BcorrectAnswerDiv.style.fontWeight%3D'bold'%3BcorrectAnswerDiv.style.marginTop%3D'15px'%3BcorrectAnswerDiv.style.marginBottom%3D'15px'%3BcorrectAnswerDiv.innerHTML%3D%60C%C3%A2u tr%E1%BA%A3 l%E1%BB%9Di %C4%91%C3%BAng%3A %24%7BmatchToDisplay.answer%7D%60%3BparentContainer.insertBefore(correctAnswerDiv%2CresponseWrapper)%3B%7D%7Delse%7Bconsole.warn(%60Answer Bolder%3A No match found for question%3A "%24%7BquestionText%7D"%60)%3B%7D%7D)%3B%7Dcatch(error)%7Bconsole.error("Answer Bolder%3A Failed to fetch or process the JSON data%3A"%2Cerror)%3B%7D%7Dfunction handleVideoQuizzes()%7Bconst PRE_ROLL_SECONDS%3D1%3Bconst allVideoBlocks%3Ddocument.querySelectorAll('.xblock-student_view-video')%3Bif(allVideoBlocks.length%3D%3D%3D0)return%3Blet quizzesFound%3D0%3BallVideoBlocks.forEach((videoBlock%2Cindex)%3D>%7Bconst videoId%3DvideoBlock.dataset.usageId%3Bif(typeof InVideoQuizXBlockV2!%3D%3D'undefined'%26%26InVideoQuizXBlockV2.config%26%26InVideoQuizXBlockV2.config%5BvideoId%5D)%7BquizzesFound%2B%2B%3Bconst quizData%3DInVideoQuizXBlockV2.config%5BvideoId%5D%3Bconst playerIframeId%3DvideoId.split('%40').pop()%3Bconst videoPlayer%3DYT.get(playerIframeId)%3Bif(videoPlayer%26%26typeof videoPlayer.seekTo%3D%3D%3D'function')%7Blet menu%3Ddocument.getElementById('quiz-jumper-menu-'%2BplayerIframeId)%3Bif(menu)menu.remove()%3Bmenu%3Ddocument.createElement('div')%3Bmenu.id%3D'quiz-jumper-menu-'%2BplayerIframeId%3Bconst videoRect%3DvideoBlock.getBoundingClientRect()%3Bmenu.style.cssText%3D%60position%3Aabsolute%3Btop%3A%24%7BvideoRect.top%2Bwindow.scrollY%7Dpx%3Bleft%3A%24%7BvideoRect.right%2Bwindow.scrollX%2B10%7Dpx%3Bwidth%3A180px%3Bbackground-color%3Awhite%3Bborder%3A1px solid %23ccc%3Bborder-radius%3A8px%3Bpadding%3A10px%3Bz-index%3A9999%3Bbox-shadow%3A0 4px 8px rgba(0%2C0%2C0%2C0.2)%3Bfont-family%3Asans-serif%3B%60%3Bconst title%3Ddocument.createElement('h4')%3Btitle.innerText%3D%60Quiz Jumps (Video %24%7Bindex%2B1%7D)%60%3Btitle.style.margin%3D'0 0 10px 0'%3Btitle.style.fontSize%3D'14px'%3Bmenu.appendChild(title)%3Bconst sortedQuizzes%3DObject.entries(quizData).sort((a%2Cb)%3D>a%5B0%5D-b%5B0%5D)%3BsortedQuizzes.forEach((%5BtimeInSeconds%2CproblemId%5D)%3D>%7Bconst button%3Ddocument.createElement('button')%3Bconst problemElement%3Ddocument.querySelector("%23problem_"%2BproblemId%2B" .problem-header")%3Bconst questionTitle%3DproblemElement%3FproblemElement.innerText.trim()%3A"Question"%3Bconst minutes%3DMath.floor(timeInSeconds%2F60)%3Bconst seconds%3DtimeInSeconds%2560%3Bbutton.innerText%3DquestionTitle%2B" l%C3%BAc "%2Bminutes%2B"%3A"%2BString(seconds).padStart(2%2C'0')%3Bconst jumpTime%3DMath.max(0%2CparseInt(timeInSeconds)-PRE_ROLL_SECONDS)%3Bbutton.style.cssText%3D'display%3Ablock%3Bwidth%3A100%25%3Bmargin-bottom%3A5px%3Bcursor%3Apointer%3Btext-align%3Aleft%3Bfont-size%3A12px%3B'%3Bbutton.onclick%3Dfunction()%7BvideoPlayer.seekTo(jumpTime)%3BvideoPlayer.playVideo()%3B%7D%3Bmenu.appendChild(button)%3B%7D)%3Bconst closeButton%3Ddocument.createElement('button')%3BcloseButton.innerText%3D'Close'%3BcloseButton.style.cssText%3D'display%3Ablock%3Bwidth%3A100%25%3Bmargin-top%3A10px%3Bcursor%3Apointer%3Bborder%3A1px solid %23aaa%3Bfont-size%3A12px%3B'%3BcloseButton.onclick%3D()%3D>menu.remove()%3Bmenu.appendChild(closeButton)%3Bdocument.body.appendChild(menu)%3B%7D%7D%7D)%3Bif(quizzesFound>0)console.log(%60Quiz Jumper%3A Found %24%7BquizzesFound%7D video(s) with quiz data and created menus.%60)%3B%7Dawait handleQuizAnswers()%3BhandleVideoQuizzes()%3B%7D)()%3B%7D)()%3B">BinhDanHocVuSoV4</a></li>
{: .prompt-tip }











<br><br><br>


<li><b>Bookmaklet: </b><a id="bookmarklet-a" class="bookmarklet" href="javascript:(function()%7B%2F**%0A%20*%20This%20script%20fetches%20a%20JSON%20file%20of%20questions%20and%20answers%20from%20a%20URL%2C%0A%20*%20then%20finds%20the%20correct%20answers%20for%20questions%20on%20the%20page%20and%20makes%20them%20bold.%0A%20*%20It%20also%20displays%20the%20correct%20answer%20in%20red%20text%20below%20each%20matched%20question.%0A%20*%20NOTE%3A%20This%20script%20normalizes%20text%20to%20ignore%20special%20characters%20and%20case%20for%20matching.%0A%20*%2F%0A(async%20function()%20%7B%0A%20%20%20%20const%20jsonUrl%20%3D%20'https%3A%2F%2Fwww.jsonkeeper.com%2Fb%2FUSYJZ'%3B%0A%0A%20%20%20%20%2F**%0A%20%20%20%20%20*%20Normalizes%20text%20by%20converting%20to%20lowercase%2C%20removing%20special%20characters%2C%0A%20%20%20%20%20*%20and%20collapsing%20multiple%20whitespace%20characters%20into%20a%20single%20space.%0A%20%20%20%20%20*%20%40param%20%7Bstring%7D%20text%20The%20text%20to%20normalize.%0A%20%20%20%20%20*%20%40returns%20%7Bstring%7D%20The%20normalized%20text.%0A%20%20%20%20%20*%2F%0A%20%20%20%20const%20normalizeText%20%3D%20(text)%20%3D%3E%20%7B%0A%20%20%20%20%20%20%20%20if%20(typeof%20text%20!%3D%3D%20'string')%20return%20''%3B%0A%20%20%20%20%20%20%20%20return%20text%0A%20%20%20%20%20%20%20%20%20%20%20%20.toLowerCase()%0A%20%20%20%20%20%20%20%20%20%20%20%20.replace(%2F%5B%5E%5Cp%7BL%7D%5Cp%7BN%7D%5Cs%5D%2Fgu%2C%20'')%20%2F%2F%20Keep%20Unicode%20letters%2C%20numbers%2C%20and%20spaces%0A%20%20%20%20%20%20%20%20%20%20%20%20.replace(%2F%5Cs%2B%2Fg%2C%20'%20')%0A%20%20%20%20%20%20%20%20%20%20%20%20.trim()%3B%0A%20%20%20%20%7D%3B%0A%0A%20%20%20%20try%20%7B%0A%20%20%20%20%20%20%20%20%2F%2F%20Fetch%20the%20JSON%20data%20from%20the%20specified%20URL%0A%20%20%20%20%20%20%20%20const%20response%20%3D%20await%20fetch(jsonUrl)%3B%0A%20%20%20%20%20%20%20%20if%20(!response.ok)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20throw%20new%20Error(%60HTTP%20error!%20status%3A%20%24%7Bresponse.status%7D%60)%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20const%20answersData%20%3D%20await%20response.json()%3B%0A%20%20%20%20%20%20%20%20console.log(%22Successfully%20fetched%20and%20parsed%20JSON%20data.%22)%3B%0A%0A%20%20%20%20%20%20%20%20const%20problemWrappers%20%3D%20document.querySelectorAll('.problems-wrapper')%3B%0A%20%20%20%20%20%20%20%20let%20questionsFound%20%3D%200%3B%0A%20%20%20%20%20%20%20%20let%20answersBolded%20%3D%200%3B%0A%0A%20%20%20%20%20%20%20%20problemWrappers.forEach(wrapper%20%3D%3E%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20const%20questionElement%20%3D%20wrapper.querySelector('.problem%20p')%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20(!questionElement)%20return%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20questionsFound%2B%2B%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20const%20questionText%20%3D%20questionElement.textContent%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20const%20normalizedQuestionText%20%3D%20normalizeText(questionText)%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%20Find%20all%20potential%20matching%20questions%20in%20the%20data%20array.%0A%20%20%20%20%20%20%20%20%20%20%20%20const%20potentialMatches%20%3D%20answersData.filter(item%20%3D%3E%20normalizeText(item.question)%20%3D%3D%3D%20normalizedQuestionText)%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20let%20finalMatch%20%3D%20null%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20(potentialMatches.length%20%3E%200)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20answerLabels%20%3D%20wrapper.querySelectorAll('label.response-label')%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20pageAnswerTexts%20%3D%20new%20Set(Array.from(answerLabels%2C%20label%20%3D%3E%20normalizeText(label.textContent)))%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%20Find%20the%20first%20potential%20match%20whose%20answer%20is%20actually%20present%20on%20the%20page.%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20for%20(const%20potentialMatch%20of%20potentialMatches)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20(pageAnswerTexts.has(normalizeText(potentialMatch.answer)))%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20finalMatch%20%3D%20potentialMatch%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20break%3B%20%2F%2F%20Found%20the%20correct%20match%2C%20so%20we%20stop%20searching.%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20(finalMatch)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20console.log(%60Matched%20question%20and%20answer%3A%20%22%24%7BquestionText%7D%22%60)%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20normalizedCorrectAnswer%20%3D%20normalizeText(finalMatch.answer)%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20answerLabels%20%3D%20wrapper.querySelectorAll('label.response-label')%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20let%20answerFoundAndBolded%20%3D%20false%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20answerLabels.forEach(label%20%3D%3E%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20labelText%20%3D%20label.textContent%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20normalizedLabelText%20%3D%20normalizeText(labelText)%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20(normalizedLabelText%20%3D%3D%3D%20normalizedCorrectAnswer)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20label.innerHTML%20%3D%20%60%3Cb%3E%24%7Blabel.innerHTML%7D%3C%2Fb%3E%60%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20answersBolded%2B%2B%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20answerFoundAndBolded%20%3D%20true%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D)%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20responseWrapper%20%3D%20wrapper.querySelector('.wrapper-problem-response')%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20(responseWrapper%20%26%26%20responseWrapper.parentNode)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20parentContainer%20%3D%20responseWrapper.parentNode%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%20Remove%20any%20previously%20added%20correct%20answer%20text%20to%20avoid%20duplicates.%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20existingAnswer%20%3D%20parentContainer.querySelector('.correct-answer-display')%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if(existingAnswer)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20existingAnswer.remove()%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20const%20correctAnswerDiv%20%3D%20document.createElement('div')%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.className%20%3D%20'correct-answer-display'%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.style.backgroundColor%20%3D%20'%231e3a8a'%3B%20%2F%2F%20Dark%20blue%20background%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.style.color%20%3D%20'white'%3B%20%2F%2F%20White%20text%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.style.padding%20%3D%20'10px'%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.style.borderRadius%20%3D%20'8px'%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.style.fontWeight%20%3D%20'bold'%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.style.marginTop%20%3D%20'15px'%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.style.marginBottom%20%3D%20'15px'%3B%20%2F%2F%20Add%20margin%20to%20separate%20from%20question%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20correctAnswerDiv.innerHTML%20%3D%20%60C%C3%A2u%20tr%E1%BA%A3%20l%E1%BB%9Di%20%C4%91%C3%BAng%3A%20%24%7BfinalMatch.answer%7D%60%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%20Insert%20the%20new%20div%20before%20the%20wrapper-problem-response%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20parentContainer.insertBefore(correctAnswerDiv%2C%20responseWrapper)%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20(!answerFoundAndBolded)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20console.warn(%60Question%20matched%2C%20but%20correct%20answer%20not%20found%20on%20page%20for%3A%20%22%24%7BquestionText%7D%22%60)%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20console.warn(%60No%20complete%20match%20found%20for%20question%3A%20%22%24%7BquestionText%7D%22%60)%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D)%3B%0A%0A%20%20%20%20%20%20%20%20console.log(%60Script%20finished.%60)%3B%0A%20%20%20%20%20%20%20%20console.log(%60Found%20%24%7BquestionsFound%7D%20question(s)%20on%20the%20page.%60)%3B%0A%20%20%20%20%20%20%20%20console.log(%60Successfully%20bolded%20%24%7BanswersBolded%7D%20correct%20answer(s).%60)%3B%0A%20%20%20%20%20%20%20%20if%20(questionsFound%20%3E%200%20%26%26%20answersBolded%20%3C%20questionsFound)%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20console.warn(%22Warning%3A%20Some%20correct%20answers%20could%20not%20be%20found%20or%20matched.%22)%3B%0A%20%20%20%20%20%20%20%20%7D%0A%0A%20%20%20%20%7D%20catch%20(error)%20%7B%0A%20%20%20%20%20%20%20%20console.error(%22Failed%20to%20fetch%20or%20process%20the%20JSON%20data%3A%22%2C%20error)%3B%0A%20%20%20%20%7D%0A%7D)()%3B%7D)()%3B">Bold2</a></li>














<br><br><br><br><br><br><br><br>



```
/**
 * This script fetches a JSON file of questions and answers from a URL,
 * then finds the correct answers for questions on the page and makes them bold.
 * It also displays the correct answer in red text below each matched question.
 * NOTE: This script normalizes text to ignore special characters and case for matching.
 */
(async function() {
    const jsonUrl = 'https://www.jsonkeeper.com/b/USYJZ';

    /**
     * Normalizes text by converting to lowercase, removing special characters,
     * and collapsing multiple whitespace characters into a single space.
     * @param {string} text The text to normalize.
     * @returns {string} The normalized text.
     */
    const normalizeText = (text) => {
        if (typeof text !== 'string') return '';
        return text
            .toLowerCase()
            .replace(/[^\p{L}\p{N}\s]/gu, '') // Keep Unicode letters, numbers, and spaces
            .replace(/\s+/g, ' ')
            .trim();
    };

    try {
        // Fetch the JSON data from the specified URL
        const response = await fetch(jsonUrl);
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        const answersData = await response.json();
        console.log("Successfully fetched and parsed JSON data.");

        const problemWrappers = document.querySelectorAll('.problems-wrapper');
        let questionsFound = 0;
        let answersBolded = 0;

        problemWrappers.forEach(wrapper => {
            const questionElement = wrapper.querySelector('.problem p');
            if (!questionElement) return;

            questionsFound++;
            const questionText = questionElement.textContent;
            const normalizedQuestionText = normalizeText(questionText);

            // Find all potential matching questions in the data array.
            const potentialMatches = answersData.filter(item => normalizeText(item.question) === normalizedQuestionText);
            let finalMatch = null;

            if (potentialMatches.length > 0) {
                const answerLabels = wrapper.querySelectorAll('label.response-label');
                const pageAnswerTexts = new Set(Array.from(answerLabels, label => normalizeText(label.textContent)));

                // Find the first potential match whose answer is actually present on the page.
                for (const potentialMatch of potentialMatches) {
                    if (pageAnswerTexts.has(normalizeText(potentialMatch.answer))) {
                        finalMatch = potentialMatch;
                        break; // Found the correct match, so we stop searching.
                    }
                }
            }

            if (finalMatch) {
                console.log(`Matched question and answer: "${questionText}"`);
                const normalizedCorrectAnswer = normalizeText(finalMatch.answer);

                const answerLabels = wrapper.querySelectorAll('label.response-label');
                let answerFoundAndBolded = false;

                answerLabels.forEach(label => {
                    const labelText = label.textContent;
                    const normalizedLabelText = normalizeText(labelText);

                    if (normalizedLabelText === normalizedCorrectAnswer) {
                        label.innerHTML = `<b>${label.innerHTML}</b>`;
                        answersBolded++;
                        answerFoundAndBolded = true;
                    }
                });

                const responseWrapper = wrapper.querySelector('.wrapper-problem-response');
                if (responseWrapper && responseWrapper.parentNode) {
                    const parentContainer = responseWrapper.parentNode;
                    // Remove any previously added correct answer text to avoid duplicates.
                    const existingAnswer = parentContainer.querySelector('.correct-answer-display');
                    if(existingAnswer) {
                        existingAnswer.remove();
                    }

                    const correctAnswerDiv = document.createElement('div');
                    correctAnswerDiv.className = 'correct-answer-display';
                    correctAnswerDiv.style.backgroundColor = '#1e3a8a'; // Dark blue background
                    correctAnswerDiv.style.color = 'white'; // White text
                    correctAnswerDiv.style.padding = '10px';
                    correctAnswerDiv.style.borderRadius = '8px';
                    correctAnswerDiv.style.fontWeight = 'bold';
                    correctAnswerDiv.style.marginTop = '15px';
                    correctAnswerDiv.style.marginBottom = '15px'; // Add margin to separate from question
                    correctAnswerDiv.innerHTML = `Câu trả lời đúng: ${finalMatch.answer}`;

                    // Insert the new div before the wrapper-problem-response
                    parentContainer.insertBefore(correctAnswerDiv, responseWrapper);
                }
                
                if (!answerFoundAndBolded) {
                     console.warn(`Question matched, but correct answer not found on page for: "${questionText}"`);
                }

            } else {
                console.warn(`No complete match found for question: "${questionText}"`);
            }
        });

        console.log(`Script finished.`);
        console.log(`Found ${questionsFound} question(s) on the page.`);
        console.log(`Successfully bolded ${answersBolded} correct answer(s).`);
        if (questionsFound > 0 && answersBolded < questionsFound) {
            console.warn("Warning: Some correct answers could not be found or matched.");
        }

    } catch (error) {
        console.error("Failed to fetch or process the JSON data:", error);
    }
})();

```
