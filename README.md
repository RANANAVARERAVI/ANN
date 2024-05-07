def McCulloch(input1, input2, w1, w2, threshold):
    weighted_sum = (w1 * input1) + (w2 * input2)
    if weighted_sum >= threshold:
        return 1
    else:
        return 0
w1 = 0.5
w2 = -0.5
threshold = -0.5
learning_rate = 0.1
target_outputs = [0, 0, 1, 0]
epochs = 1000
for epoch in range(epochs):
    for inputs, target_output in zip([(0, 0), (0, 1), (1, 0), (1, 1)], target_outputs):
        input1, input2 = inputs
        output = McCulloch(input1, input2, w1, w2, threshold)
        error = target_output - output
        w1 += learning_rate * error * input1
        w2 += learning_rate * error * input2
        threshold -= learning_rate * error
print("ANDNOT(0, 0) =", McCulloch(0, 0, w1, w2, threshold))
print("ANDNOT(0, 1) =", McCulloch(0, 1, w1, w2, threshold))
print("ANDNOT(1, 0) =", McCulloch(1, 0, w1, w2, threshold))
print("ANDNOT(1, 1) =", McCulloch(1, 1, w1, w2, threshold))
print(f"Weights:w1 = {w1}\n\tw2 = {w2}\nThreshold : {threshold}")
