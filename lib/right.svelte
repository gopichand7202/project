<script>
    import {
      Form,
      FormGroup,
      Select,
      SelectItem,
      Button,
      TextInput
    } from "carbon-components-svelte";
  </script>
  
  <style>
    .right-form {
      height: 75vh;
      padding: 30px;
      display: flex;
      justify-content: center;
      align-items: center;
      box-sizing: border-box;
      border-left: 1px solid #ccc;
    }
    /* form {
      width: 100%;
      display: flex;
      flex-direction: column;
      gap:2px;
    } */
    /* Responsive behavior */
    @media (max-width: 768px) {
      .right-form {
        padding: 10px;
      }
    }
  </style>
  
  <div class="right-form">
    <div class="form">
    <Form on:submit>
      <!-- Carbon handles the label inside the Select component -->
      <FormGroup>
        <Select id="select-1" labelText="Country">
          <SelectItem disabled hidden value="" text="" />
          <SelectItem value="India" text="India" />
          <SelectItem value="Pakistan" text="Pakistan" />
          <SelectItem value="China" text="China" />
        </Select>
      </FormGroup>
  
      <!-- TextInput fields with inline labels handled by Carbon -->
      <TextInput id="radarid" labelText="Radar ID" />
      <TextInput id="fov" labelText="FOV" />
      <TextInput id="fusionid" labelText="Fusion ID" />
      <TextInput id="sessionID" labelText="Session ID" />
  
      <Button type="submit" style="margin-top: 20px;">Submit</Button>
    </Form>
</div>
  </div>
  