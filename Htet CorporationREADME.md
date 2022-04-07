- 👋 Hi, I’m @htetnaingsoe25
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
htetnaingsoe25/htetnaingsoe25 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
https://github.com/webcompat/web-bugs/issues/53569
let map: google.maps.Map;
let marker: google.maps.Marker;
let geocoder: google.maps.Geocoder;
let responseDiv: HTMLDivElement;
let response: HTMLPreElement;

function initMap(): void {
  map = new google.maps.Map(document.getElementById("map") as HTMLElement, {
    zoom: 8,
    center: { lat: -34.397, lng: 150.644 },
    mapTypeControl: false,
  });
  geocoder = new google.maps.Geocoder();

  const inputText = document.createElement("input");

  inputText.type = "text";
  inputText.placeholder = "Enter a location";

  const submitButton = document.createElement("input");

  submitButton.type = "button";
  submitButton.value = "Geocode";
  submitButton.classList.add("button", "button-primary");

  const clearButton = document.createElement("input");

  clearButton.type = "button";
  clearButton.value = "Clear";
  clearButton.classList.add("button", "button-secondary");

  response = document.createElement("pre");
  response.id = "response";
  response.innerText = "";

  responseDiv = document.createElement("div");
  responseDiv.id = "response-container";
  responseDiv.appendChild(response);

  const instructionsElement = document.createElement("p");

  instructionsElement.id = "instructions";

  instructionsElement.innerHTML =
    "<strong>Instructions</strong>: Enter an address in the textbox to geocode or click on the map to reverse geocode.";

  map.controls[google.maps.ControlPosition.TOP_LEFT].push(inputText);
  map.controls[google.maps.ControlPosition.TOP_LEFT].push(submitButton);
  map.controls[google.maps.ControlPosition.TOP_LEFT].push(clearButton);
  map.controls[google.maps.ControlPosition.LEFT_TOP].push(instructionsElement);
  map.controls[google.maps.ControlPosition.LEFT_TOP].push(responseDiv);

  marker = new google.maps.Marker({
    map,
  });

  map.addListener("click", (e: google.maps.MapMouseEvent) => {
    geocode({ location: e.latLng });
  });

  submitButton.addEventListener("click", () =>
    geocode({ address: inputText.value })
  );

  clearButton.addEventListener("click", () => {
    clear();
  });

  clear();
}

function clear() {
  marker.setMap(null);
  responseDiv.style.display = "none";
}

function geocode(request: google.maps.GeocoderRequest): void {
  clear();

  geocoder
    .geocode(request)
    .then((result) => {
      const { results } = result;

      map.setCenter(results[0].geometry.location);
      marker.setPosition(results[0].geometry.location);
      marker.setMap(map);
      responseDiv.style.display = "block";
      response.innerText = JSON.stringify(result, null, 2);
      return results;
    })
    .catch((e) => {
      alert("Geocode was not successful for the following reason: " + e);
    });
}

Use two fingers to move the map

Instructions: Enter an address in the textbox to geocode or click on the map to reverse geocode.

{
"results": [
{
"address_components": [
{
"long_name": "Myanmar (Burma)",
"short_name": "MM",
"types": [
"country",
"political"
]
}
],
"formatted_address": "Myanmar (Burma)",
"geometry": {
"bounds": {
"south": 9.4518,
"west": 92.171808,
"north": 28.5478351,
"east": 101.1702717
},
"location": {
"lat": 21.916221,
"lng": 95.955974
},
"location_type": "APPROXIMATE",
"viewport": {
"south": 9.4518,
"west": 92.171808,
"north": 28.5478351,
"east": 101.1702717
}
},
Quantization of Image Classification Models — OpenVINO™ documentation — Version(latest)

docs.openvino.ai

graph(%input.1 : Float(1:3072, 3:1024, 32:32, 32:1, requires_grad=0, device=cpu), %classifier.1.weight : Float(10:1280, 1280:1, requires_grad=1, device=cpu), %classifier.1.bias : Float(10:1, requires_grad=1, device=cpu), %468 : Float(32:27, 3:9, 3:3, 3:1, requires_grad=0, device=cpu), %469 : Float(32:1, requires_grad=0, device=cpu), %471 : Float(32:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %472 : Float(32:1, requires_grad=0, device=cpu), %474 : Float(16:32, 32:1, 1:1, 1:1, requires_grad=0, device=cpu), %475 : Float(16:1, requires_grad=0, device=cpu), %477 : Float(96:16, 16:1, 1:1, 1:1, requires_grad=0, device=cpu), %478 : Float(96:1, requires_grad=0, device=cpu), %480 : Float(96:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %481 : Float(96:1, requires_grad=0, device=cpu), %483 : Float(24:96, 96:1, 1:1, 1:1, requires_grad=0, device=cpu), %484 : Float(24:1, requires_grad=0, device=cpu), %486 : Float(144:24, 24:1, 1:1, 1:1, requires_grad=0, device=cpu), %487 : Float(144:1, requires_grad=0, device=cpu), %489 : Float(144:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %490 : Float(144:1, requires_grad=0, device=cpu), %492 : Float(24:144, 144:1, 1:1, 1:1, requires_grad=0, device=cpu), %493 : Float(24:1, requires_grad=0, device=cpu), %495 : Float(144:24, 24:1, 1:1, 1:1, requires_grad=0, device=cpu), %496 : Float(144:1, requires_grad=0, device=cpu), %498 : Float(144:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %499 : Float(144:1, requires_grad=0, device=cpu), %501 : Float(32:144, 144:1, 1:1, 1:1, requires_grad=0, device=cpu), %502 : Float(32:1, requires_grad=0, device=cpu), %504 : Float(192:32, 32:1, 1:1, 1:1, requires_grad=0, device=cpu), %505 : Float(192:1, requires_grad=0, device=cpu), %507 : Float(192:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %508 : Float(192:1, requires_grad=0, device=cpu), %510 : Float(32:192, 192:1, 1:1, 1:1, requires_grad=0, device=cpu), %511 : Float(32:1, requires_grad=0, device=cpu), %513 : Float(192:32, 32:1, 1:1, 1:1, requires_grad=0, device=cpu), %514 : Float(192:1, requires_grad=0, device=cpu), %516 : Float(192:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %517 : Float(192:1, requires_grad=0, device=cpu), %519 : Float(32:192, 192:1, 1:1, 1:1, requires_grad=0, device=cpu), %520 : Float(32:1, requires_grad=0, device=cpu), %522 : Float(192:32, 32:1, 1:1, 1:1, requires_grad=0, device=cpu), %523 : Float(192:1, requires_grad=0, device=cpu), %525 : Float(192:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %526 : Float(192:1, requires_grad=0, device=cpu), %528 : Float(64:192, 192:1, 1:1, 1:1, requires_grad=0, device=cpu), %529 : Float(64:1, requires_grad=0, device=cpu), %531 : Float(384:64, 64:1, 1:1, 1:1, requires_grad=0, device=cpu), %532 : Float(384:1, requires_grad=0, device=cpu), %534 : Float(384:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %535 : Float(384:1, requires_grad=0, device=cpu), %537 : Float(64:384, 384:1, 1:1, 1:1, requires_grad=0, device=cpu), %538 : Float(64:1, requires_grad=0, device=cpu), %540 : Float(384:64, 64:1, 1:1, 1:1, requires_grad=0, device=cpu), %541 : Float(384:1, requires_grad=0, device=cpu), %543 : Float(384:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %544 : Float(384:1, requires_grad=0, device=cpu), %546 : Float(64:384, 384:1, 1:1, 1:1, requires_grad=0, device=cpu), %547 : Float(64:1, requires_grad=0, device=cpu), %549 : Float(384:64, 64:1, 1:1, 1:1, requires_grad=0, device=cpu), %550 : Float(384:1, requires_grad=0, device=cpu), %552 : Float(384:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %553 : Float(384:1, requires_grad=0, device=cpu), %555 : Float(64:384, 384:1, 1:1, 1:1, requires_grad=0, device=cpu), %556 : Float(64:1, requires_grad=0, device=cpu), %558 : Float(384:64, 64:1, 1:1, 1:1, requires_grad=0, device=cpu), %559 : Float(384:1, requires_grad=0, device=cpu), %561 : Float(384:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %562 : Float(384:1, requires_grad=0, device=cpu), %564 : Float(96:384, 384:1, 1:1, 1:1, requires_grad=0, device=cpu), %565 : Float(96:1, requires_grad=0, device=cpu), %567 : Float(576:96, 96:1, 1:1, 1:1, requires_grad=0, device=cpu), %568 : Float(576:1, requires_grad=0, device=cpu), %570 : Float(576:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %571 : Float(576:1, requires_grad=0, device=cpu), %573 : Float(96:576, 576:1, 1:1, 1:1, requires_grad=0, device=cpu), %574 : Float(96:1, requires_grad=0, device=cpu), %576 : Float(576:96, 96:1, 1:1, 1:1, requires_grad=0, device=cpu), %577 : Float(576:1, requires_grad=0, device=cpu), %579 : Float(576:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %580 : Float(576:1, requires_grad=0, device=cpu), %582 : Float(96:576, 576:1, 1:1, 1:1, requires_grad=0, device=cpu), %583 : Float(96:1, requires_grad=0, device=cpu), %585 : Float(576:96, 96:1, 1:1, 1:1, requires_grad=0, device=cpu), %586 : Float(576:1, requires_grad=0, device=cpu), %588 : Float(576:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %589 : Float(576:1, requires_grad=0, device=cpu), %591 : Float(160:576, 576:1, 1:1, 1:1, requires_grad=0, device=cpu), %592 : Float(160:1, requires_grad=0, device=cpu), %594 : Float(960:160, 160:1, 1:1, 1:1, requires_grad=0, device=cpu), %595 : Float(960:1, requires_grad=0, device=cpu), %597 : Float(960:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %598 : Float(960:1, requires_grad=0, device=cpu), %600 : Float(160:960, 960:1, 1:1, 1:1, requires_grad=0, device=cpu), %601 : Float(160:1, requires_grad=0, device=cpu), %603 : Float(960:160, 160:1, 1:1, 1:1, requires_grad=0, device=cpu), %604 : Float(960:1, requires_grad=0, device=cpu), %606 : Float(960:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %607 : Float(960:1, requires_grad=0, device=cpu), %609 : Float(160:960, 960:1, 1:1, 1:1, requires_grad=0, device=cpu), %610 : Float(160:1, requires_grad=0, device=cpu), %612 : Float(960:160, 160:1, 1:1, 1:1, requires_grad=0, device=cpu), %613 : Float(960:1, requires_grad=0, device=cpu), %615 : Float(960:9, 1:9, 3:3, 3:1, requires_grad=0, device=cpu), %616 : Float(960:1, requires_grad=0, device=cpu), %618 : Float(320:960, 960:1, 1:1, 1:1, requires_grad=0, device=cpu), %619 : Float(320:1, requires_grad=0, device=cpu), %621 : Float(1280:320, 320:1, 1:1, 1:1, requires_grad=0, device=cpu), %622 : Float(1280:1, requires_grad=0, device=cpu)): %467 : Float(1:32768, 32:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[1, 1]](%input.1, %468, %469) %317 : Float(1:32768, 32:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%467) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %470 : Float(1:32768, 32:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=32, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[1, 1]](%317, %471, %472) %320 : Float(1:32768, 32:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%470) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %473 : Float(1:16384, 16:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%320, %474, %475) %476 : Float(1:98304, 96:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%473, %477, %478) %325 : Float(1:98304, 96:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%476) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %479 : Float(1:98304, 96:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=96, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[1, 1]](%325, %480, %481) %328 : Float(1:98304, 96:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%479) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %482 : Float(1:24576, 24:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%328, %483, %484) %485 : Float(1:147456, 144:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%482, %486, %487) %333 : Float(1:147456, 144:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%485) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %488 : Float(1:147456, 144:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=144, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[1, 1]](%333, %489, %490) %336 : Float(1:147456, 144:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%488) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %491 : Float(1:24576, 24:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%336, %492, %493) %339 : Float(1:24576, 24:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Add(%482, %491) # /opt/home/k8sworker/.cache/torch/hub/chenyaofo_pytorch-cifar-models_master/pytorch_cifar_models/mobilenetv2.py:144:0 %494 : Float(1:147456, 144:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%339, %495, %496) %342 : Float(1:147456, 144:1024, 32:32, 32:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%494) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %497 : Float(1:36864, 144:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=144, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[2, 2]](%342, %498, %499) %345 : Float(1:36864, 144:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%497) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %500 : Float(1:8192, 32:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%345, %501, %502) %503 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%500, %504, %505) %350 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%503) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %506 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=192, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[1, 1]](%350, %507, %508) %353 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%506) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %509 : Float(1:8192, 32:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%353, %510, %511) %356 : Float(1:8192, 32:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Add(%500, %509) # /opt/home/k8sworker/.cache/torch/hub/chenyaofo_pytorch-cifar-models_master/pytorch_cifar_models/mobilenetv2.py:144:0 %512 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%356, %513, %514) %359 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%512) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %515 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=192, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[1, 1]](%359, %516, %517) %362 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%515) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %518 : Float(1:8192, 32:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%362, %519, %520) %365 : Float(1:8192, 32:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Add(%356, %518) # /opt/home/k8sworker/.cache/torch/hub/chenyaofo_pytorch-cifar-models_master/pytorch_cifar_models/mobilenetv2.py:144:0 %521 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0], strides=[1, 1]](%365, %522, %523) %368 : Float(1:49152, 192:256, 16:16, 16:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%521) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %524 : Float(1:12288, 192:64, 8:8, 8:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=192, kernel_shape=[3, 3], pads=[1, 1, 1, 1], strides=[2, 2]](%368, %525, %526) %371 : Float(1:12288, 192:64, 8:8, 8:1, requires_grad=1, device=cpu) = onnx::Clip[max=6., min=0.](%524) # /opt/home/k8sworker/cibuilds/ov-notebook/OVNotebookOps-104/.workspace/scm/ov-notebook/.venv/lib/python3.8/site-packages/torch/nn/functional.py:1186:0 %527 : Float(1:4096, 64:64, 8:8, 8:1, requires_grad=1, device=cpu) = onnx::Conv[dilations=[1, 1], group=1, kernel_shape=[1, 1], pads=[0, 0, 0, 0


