
## Training Process
1. Creating the dataset: `data = ImageDataBunch`
    - `data.classes`: classes for the data
    - `data.c`: all possible labels in the data
2. Create the cnn: `learn = create_cnn`
3. Train with a one cycle policy: `learn.fit_one_cycle(n)`
  - Save the model: `learn.save('name')`
4. Unfreeze the rest of the model: `learn.unfreeze()`
5. Run the learning rate finder: `learn.lr_find()`
  - Plot results: `learn.recorder.plot()`
  - Looking for the strongest downward slope that is consistent.
6. Train with a one cycle policy with the newly found learning rate
  - save the model: `learn.save('name')`
7. Interpret the results: `interp = ClassificationInterpretation`
  - `interp.top_losses()` returns the loss and index for all the dataset
  
## Classes Notes
- Dataset objects have:
  - `data.x`: thing used to get the images (on vision). When used with `top_losses()` it can be used to return the filenames of the items that have the top losses. For example: `data.valid_ds.x[idx]` where `losses, idx = interp.top_losses()` will return the filenames of the files in the validation dataset ordered by loss in descending order. 
  - `data.y`: labels for the data
  

## Lesson 2 Notes
- Look for bias in the noise of the data. Models tend to work fairly well with random noise in the data; however, biased noise in the data will affect performance.
- Production environment recommendation: CPU
- Free hosting: python anywhere (creating web apps)

### Things that can go wrong
- Learning rate is too high: this will make the validation loss huge
- Learning rate is too low: error rate gets better very slowly. Training loss will be higher than validation loss.
- When the training loss is higher than validation loss, it means the model has not been trained enough.
- Too few epochs: training loss will be higher than the validation loss. This looks similar to learning rate too low.
- Too many epochs: overfitting - error rate will improve for a while and then get worst
- Overfitting: training loss goes down and then starts increasing





