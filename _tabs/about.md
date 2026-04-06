---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---




> <li><b>Bookmaklet: </b>
  <a href="javascript:(function()%7Bjavascript%3A(function()%257B%252F**%250A%20*%20This%20script%20finds%20hidden%20in-video%20questions%20within%20the%20page%252C%250A%20*%20moves%20the%20actual%20interactive%20elements%20to%20a%20new%20section%20below%20the%20main%20video%252C%250A%20*%20and%20makes%20them%20visible%20so%20they%20can%20be%20answered%20and%20submitted.%250A%20*%20It%20strictly%20retains%20verification%20data%20by%20moving%20the%20original%20elements.%250A%20*%252F%250A(function()%20%257B%250A%20%20%20%20%252F%252F%201.%20Identify%20the%20main%20video%20component%20container%20using%20a%20class%20selector%20for%20broader%20compatibility.%250A%20%20%20%20%252F%252F%20We'll%20insert%20the%20questions%20container%20right%20after%20this%20component.%250A%20%20%20%20const%20videoComponent%20%253D%20document.querySelector('.xblock-student_view-video')%253B%250A%250A%20%20%20%20if%20(!videoComponent)%20%257B%250A%20%20%20%20%20%20%20%20console.error(%22Could%20not%20find%20the%20video%20component%20container%20on%20the%20page.%22)%253B%250A%20%20%20%20%20%20%20%20return%253B%250A%20%20%20%20%257D%250A%250A%20%20%20%20%252F%252F%20Check%20if%20the%20questions%20have%20already%20been%20moved%20to%20prevent%20duplication%250A%20%20%20%20if%20(document.getElementById('uncovered-questions-container'))%20%257B%250A%20%20%20%20%20%20%20%20console.log(%22Questions%20have%20already%20been%20uncovered%20and%20moved.%22)%253B%250A%20%20%20%20%20%20%20%20return%253B%250A%20%20%20%20%257D%250A%250A%20%20%20%20%252F%252F%202.%20Select%20all%20problem%20blocks%20that%20are%20designated%20as%20'in-video'%20problems.%250A%20%20%20%20%252F%252F%20%20%20%20These%20are%20the%20elements%20that%20are%20initially%20hidden%20from%20the%20user.%250A%20%20%20%20const%20hiddenProblemElements%20%253D%20document.querySelectorAll('.xblock-student_view-problem.in-video-problem')%253B%250A%250A%20%20%20%20if%20(hiddenProblemElements.length%20%253D%253D%253D%200)%20%257B%250A%20%20%20%20%20%20%20%20console.log(%22No%20hidden%20in-video%20questions%20were%20found%20on%20this%20page.%22)%253B%250A%20%20%20%20%20%20%20%20return%253B%250A%20%20%20%20%257D%250A%250A%20%20%20%20%252F%252F%203.%20Create%20a%20new%20container%20element%20to%20display%20the%20questions%20we%20uncover.%250A%20%20%20%20const%20questionsDisplayContainer%20%253D%20document.createElement('div')%253B%250A%20%20%20%20questionsDisplayContainer.id%20%253D%20'uncovered-questions-container'%253B%250A%20%20%20%20%252F%252F%20Apply%20some%20styling%20to%20make%20the%20new%20section%20look%20clean.%250A%20%20%20%20questionsDisplayContainer.style.cssText%20%253D%20%2560%250A%20%20%20%20%20%20%20%20padding%253A%2020px%253B%250A%20%20%20%20%20%20%20%20margin-top%253A%2025px%253B%250A%20%20%20%20%20%20%20%20border%253A%201px%20solid%20%2523e0e0e0%253B%250A%20%20%20%20%20%20%20%20border-radius%253A%208px%253B%250A%20%20%20%20%20%20%20%20background-color%253A%20%2523f9f9f9%253B%250A%20%20%20%20%20%20%20%20font-family%253A%20sans-serif%253B%250A%20%20%20%20%2560%253B%250A%20%20%20%20questionsDisplayContainer.innerHTML%20%253D%20'%3Ch3%20style%253D%22margin-top%253A%200%253B%20border-bottom%253A%202px%20solid%20%2523ccc%253B%20padding-bottom%253A%2010px%253B%22%3EInteractive%20In-Video%20Questions%3C%252Fh3%3E'%253B%250A%250A%20%20%20%20%252F%252F%204.%20Loop%20through%20each%20of%20the%20hidden%20problem%20elements%20found.%250A%20%20%20%20hiddenProblemElements.forEach((problemElement%252C%20index)%20%253D%3E%20%257B%250A%20%20%20%20%20%20%20%20%252F%252F%20ACTION%20A%253A%20Make%20the%20original%20question%20block%20visible.%250A%20%20%20%20%20%20%20%20problemElement.style.display%20%253D%20'block'%253B%250A%250A%20%20%20%20%20%20%20%20%252F%252F%20Add%20a%20separator%20for%20better%20visual%20distinction%20between%20questions.%250A%20%20%20%20%20%20%20%20if%20(index%20%3E%200)%20%257B%250A%20%20%20%20%20%20%20%20%20%20%20%20const%20separator%20%253D%20document.createElement('hr')%253B%250A%20%20%20%20%20%20%20%20%20%20%20%20separator.style.marginTop%20%253D%20'20px'%253B%250A%20%20%20%20%20%20%20%20%20%20%20%20separator.style.marginBottom%20%253D%20'20px'%253B%250A%20%20%20%20%20%20%20%20%20%20%20%20questionsDisplayContainer.appendChild(separator)%253B%250A%20%20%20%20%20%20%20%20%257D%250A%20%20%20%20%20%20%20%20%250A%20%20%20%20%20%20%20%20%252F%252F%20ACTION%20B%253A%20Move%20the%20entire%20interactive%20problem%20element%20into%20our%20new%20container.%250A%20%20%20%20%20%20%20%20%252F%252F%20This%20preserves%20its%20functionality%252C%20including%20the%20ability%20to%20select%20answers%20and%20submit.%250A%20%20%20%20%20%20%20%20questionsDisplayContainer.appendChild(problemElement)%253B%250A%20%20%20%20%257D)%253B%250A%250A%20%20%20%20%252F%252F%205.%20Find%20the%20parent%20vertical%20block%20('.vert')%20of%20the%20video%20component%250A%20%20%20%20%252F%252F%20%20%20%20and%20insert%20the%20new%20container%20right%20after%20it%20in%20the%20DOM.%20This%20ensures%250A%20%20%20%20%252F%252F%20%20%20%20the%20questions%20appear%20cleanly%20below%20the%20video%20player%20component.%250A%20%20%20%20const%20videoBlockContainer%20%253D%20videoComponent.closest('.vert')%253B%250A%20%20%20%20if%20(videoBlockContainer%20%2526%2526%20videoBlockContainer.parentNode)%20%257B%250A%20%20%20%20%20%20%20%20videoBlockContainer.parentNode.insertBefore(questionsDisplayContainer%252C%20videoBlockContainer.nextSibling)%253B%250A%20%20%20%20%257D%20else%20%257B%250A%20%20%20%20%20%20%20%20%252F%252F%20Fallback%20if%20the%20'.vert'%20structure%20isn't%20found%20for%20some%20reason.%250A%20%20%20%20%20%20%20%20videoComponent.parentNode.insertBefore(questionsDisplayContainer%252C%20videoComponent.nextSibling)%253B%250A%20%20%20%20%20%20%20%20console.warn(%22Could%20not%20find%20the%20'.vert'%20container.%20Inserting%20questions%20immediately%20after%20the%20video%20component.%22)%253B%250A%20%20%20%20%257D%250A%250A%20%20%20%20console.log(%2560Success%253A%20Found%20and%20moved%20%2524%257BhiddenProblemElements.length%257D%20interactive%20questions.%2560)%253B%250A%250A%257D)()%253B%257D)()%253B%7D)()%3B">Unlock câu hỏi</a>
  </li>
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
